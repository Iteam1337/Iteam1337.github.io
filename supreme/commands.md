# Commands

## init

- Create a base setup for [`@iteam/config`](https://github.com/Iteam1337/config).
- Initialize an empty repository and creates a `.gitignore` with some standard
  values.
- Install [`husky`](https://github.com/typicode/husky), a tool for git hooks, and setup
  it up with [`pretty-quick`](https://github.com/azz/pretty-quick) that runs
  `prettier` on staged files.
- Create `jest.config.js` and install [`jest`](https://jestjs.io/)
- Create a `.nvmrc` wih the users current node version
- Install [`prettier`](https://prettier.io/), a tool that formats JavaScript, and
  creates our preferred configuration.

#### Example

```sh
$ supreme init
```

## add

Add one of the configs/packages created by [`init`](init) inside the current
working directory.

### Valid commands

#### config

Create a base setup for [`@iteam/config`](https://github.com/Iteam1337/config)
with TypeScript.

##### Flags

- `--javascript` (optional) - create a config with JavaScript

#### gitignore / git

Initialize an empty repository and creates a `.gitignore` with some standard
values.

#### husky

Install [`husky`](https://github.com/typicode/husky), a tool for git hooks, and setup
it up with [`pretty-quick`](https://github.com/azz/pretty-quick) that runs
`prettier` on staged files.

#### jest

Create `jest.config.js` and install [`jest`](https://jestjs.io/)

#### nvm / nvmrc

Create a `.nvmrc` wih the users current node version

#### prettier

Install [`prettier`](https://prettier.io/), a tool that formats JavaScript, and
creates our preferred configuration.

#### Example

```sh
$ supreme add git
```

## react

Create a TypeScript React app using `create-react-app` with the provided name.

#### Example

```sh
$ supreme react my-awesome-app
```

#### Flags

- `--javascript` (optional) - create a JavaScript React app

## reason

Create a ReasonReact app using `bsb`, from `bs-platform`, and customize the app with our preferred defaults.

!> To use this command you will need BuckleScript and Reason, `npm i -g bs-platform`

#### Included

- ReasonReact
- Test using [`jest`](https://jestjs.io/) and
  [`react-testing-library`](https://testing-library.com/docs/react-testing-library/intro)
- [Tailwind](https://travis-ci.com/) styling
- [Travis CI](https://travis-ci.com/) configuration
- Automatic versioning using `semantic-release`
- [Now](https://zeit.co/) build (opt-in)

#### Example

```sh
$ supreme reason my-awesome-app
```

## snippets

Copy a bunch of commonly used snippets to the clipboard

| IDE         | Language   | Snippet engine                                   | IDE flag | Language flag    |
| ----------- | ---------- | ------------------------------------------------ | -------- | ---------------- |
| vim, neovim | JavaScript | [UltiSnips](https://github.com/SirVer/ultisnips) | vim      | js, javascript   |
| vim, neovim | TypeScript | [UltiSnips](https://github.com/SirVer/ultisnips) | vim      | ts, typescript   |
| vim, neovim | ReasonML   | [UltiSnips](https://github.com/SirVer/ultisnips) | vim      | reason, reasonml |

#### Flags

- `--ide` (required) - What IDE to copy snippets for
- `--language` (required) - What language to copy snippets for

#### Example

```sh
$ supreme snippets --ide=vim --language=ts
```
