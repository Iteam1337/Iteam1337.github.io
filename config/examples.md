## Priority order

The order of how the config is transformed is:

1. Defaults
1. Environment
1. Config file
1. Secrets

That means that environment variables will override defaults, and the config file will override environment variables and so on.

## Simple usage

```javascript
const config = require('@iteam/config')({
  file: `${__dirname}/../config.json`,
  defaults: {
    foo: {
      bar: 'baz',
    },
    baz: [1, 2, 3],
  },
})

config.get('foo') // { bar: 'baz' }
config.get('foo:bar') // 'baz'
config.get('baz') // [ 1, 2, 3 ]
```

## Config file

Config files override the default values

### Example

```json
// config.json
{
  "baz": [4, 5, 6]
}
```

```javascript
const config = require('@iteam/config')({
  file: `${__dirname}/../config.json`,
  defaults: {
    baz: [1, 2, 3],
  },
})

// Values from config.json override defaults
config.get('baz') // [ 4, 5, 6 ]
```

## Using environment variables

Environment variables will most often be used in CI or production environments. Environment variables override default values.

**Casing is ignored**, but the output will always be camel-cased. For example, when starting application in from terminal:

### Example

```bash
NESTED__CONFIG__IN_CAMEL_CASE=ok \
nested__secondValue=bar \
npm start
```

Will be transformed into the following result in **javascript**:

```javascript
{
  nested: {
    config: {
      inCamelCase: 'on',
    },
    secondValue: 'foo',
  }
}
```

Together with a `config.js`

```javascript
const config = require('@iteam/config')({
  file: `${__dirname}/../config.json`,
  defaults: {
    nested: {
      config: {
        inCamelCase: 'off',
      },
      secondValue: 'bar',
    },
  },
})

// Values received from environment variables override defaults
config.get('nested:config:inCamelCase') // 'on'
config.get('nested:secondValue') // 'foo'
```

## Secrets

This module got extended with `docker-swarm` in mind, and their way of handling secrects (which is run-time mounted files).

### Example

The directory `/run/secrets` has these file in it:

```sh
some_nested__file
some_nested__other_file
```

When they are provided to the module they will be transformed as such:

```javascript
{
  someNested: {
    file: 'contents of "/run/secrets/some_nested__file"',
    otherFile: 'contents of "/run/secrets/some_nested__other_file"'
  }
}
```

To enable this, provide `secrets` as a argument when calling the module:

```javascript
const config = require('@iteam/config')({
  secrets: {
    dir: '/run/secrets/',
  },
})
```

## Using TypeScript

TypeScript is fully supported and the package includes it's own type
definitions.

### Example

```typescript
import config from '@iteam/config'

export interface PostgresConfig {
  database: string
  host: string
}

export interface Config {
  postgres: PostgresConfig
  port: number
}

const config = config({
  file: `${__dirname}/../config.json`,
  defaults: {
    port: 3000,
    postgres: {
      database: 'db',
      host: 'localhost',
    },
  },
})

export default {
  postgres: config.get('fortnox'),
  port: config.get('port'),
} as Config
```

## Options

```typescript
{
  defaults?: {
    [key: string]: any
  }
  env?: { separator?: string }
  file?: string | { search?: string, dir?: string, file?: string }
  secrets?: false | { dir?: string, separator?: string } | string
}
```

#### defaults

```typescript
{
  [key: string]: any
}
```

#### env

```typescript
{
  separator: string // default: '__'
}
```

#### file

When providing a `string`, this should point to the full location of the config-file, or the `dir` will be the default

```typescript
{
  search?: boolean // default: false
  dir?: string // default: '../'
  file?: string // default: 'config.json'
}
```

#### secrets

When providing a `string`, this should be the directory where secrets are stored. The object form takes two properties:

```typescript
{
  dir?: string // default: '/run/secrets/'
  separator?: string // default: '__'
}
```

