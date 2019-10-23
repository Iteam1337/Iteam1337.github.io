# ESLint

We have a couple of ESLint setups with our preferred defaults

## Node

### Installation

```
npm install --save-dev @iteam/eslint-config-node
```

or use [`supreme`](https://github.com/Iteam1337/supreme)

```
npx @iteam/supreme add eslint --node
```

Then add the `@iteam/eslint-config-node` in your `.eslintrc`

```
{
  "extends": [
    "@iteam/eslint-config-node"
  ]
}
```

### Features

- ESLint recommended settings
- Prettier

## React

### Installation

```
npm install --save-dev @iteam/eslint-config-react
```

or use [`supreme`](https://github.com/Iteam1337/supreme)

```
npx @iteam/supreme add eslint --react
```

Then add the `@iteam/eslint-config-react` in your `.eslintrc`

```
{
  "extends": [
    "@iteam/eslint-config-react"
  ]
}
```

### Features

- ESLint recommended settings
- React recommended settings
- Prettier
