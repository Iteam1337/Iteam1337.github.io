# Commands

## init

- Creates a base setup for [`@iteam/config`](https://github.com/Iteam1337/config).
- Initializes an empty repository and creates a `.gitignore` with some standard
  values.
- Installs [`husky`](https://github.com/typicode/husky), a tool for git hooks, and setup
  it up with [`pretty-quick`](https://github.com/azz/pretty-quick) that runs
  `prettier` on staged files.
- Create `jest.config.js` and install [`jest`](https://jestjs.io/)
- Create a `.nvmrc` wih the users current node version
- Installs [`prettier`](https://prettier.io/), a tool that formats JavaScript, and
  creates our preferred configuration.

### Example

```sh
$ supreme init
```

## add

Add one of the configs/packages created by [`init`](init) inside the current
working directory.

### Valid commands

#### config

Creates a base setup for [`@iteam/config`](https://github.com/Iteam1337/config).

#### gitignore / git

Initializes an empty repository and creates a `.gitignore` with some standard
values.

#### husky

Installs [`husky`](https://github.com/typicode/husky), a tool for git hooks, and setup
it up with [`pretty-quick`](https://github.com/azz/pretty-quick) that runs
`prettier` on staged files.

#### jest

Create `jest.config.js` and install [`jest`](https://jestjs.io/)

#### nvm / nvmrc

Create a `.nvmrc` wih the users current node version

#### prettier

Installs [`prettier`](https://prettier.io/), a tool that formats JavaScript, and
creates our preferred configuration.

### Example

```sh
$ supreme add git
```

## react

Create a React app using `create-react-app` with the provided name.

### Example

```sh
$ supreme react my-awesome-app
```

### Supported flags

- `--typescript` - create a Typescript React app

## reason

Create a ReasonReact app using `bsb`, from `bs-platform`, and customize the app with our preferred defaults.

!> To use this command you will need BuckleScript and Reason, `npm i -g bs-platform`

### Included

- ReasonReact
- Test using `bs-jest`
- Travis CI configuration
- Automatic versioning using `semantic-release`
- Now build (opt-in)

### Example

```sh
$ supreme reason my-awesome-app
```