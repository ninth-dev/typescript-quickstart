## Jest 

Jest seems to be the most popular test framework in JavaScript.

There's a few ways you can run `jest` with TypeScript. We will use `ts-jest`.

```sh
yarn add --dev jest
yarn add --dev ts-jest @types/jest
yarn ts-jest config:init
```

## Create some tests:

```sh
mkdir -p src/__tests__
touch src/__tests__/index.test.ts
```

## Add some scripts to `package.json`


```json
{
  // ---
  "scripts": {
    // ---
    "test": "jest --coverage",
    "test:watch": "jest --watch",
    // ---
  },
  // ---
}
```

## Optimise the build

```sh
yarn build
```

You will notice that `__tests__` are also getting transpiled. We dont need these.

We can try to add `exclude` key into `tsconfig.json`. However, you will soon notice this will break eslint.
We are using `type-aware` rules, `tsconfig.json` needs to include the test files.

Instead, we can split `tsconfig` into a few files.

- `tsconfig.base.json`

```json
// this tsconfig is used the language server and for testing
{
  "extends": "@tsconfig/node14/tsconfig.json",
  "compilerOptions": {
    "noUncheckedIndexedAccess": true,
    "noImplicitOverride": true,
  }
}
```

- `tsconfig.json`

```json
// this tsconfig is used the language server and for testing
{
  "extends": "tsconfig.base.json",
  "compilerOptions": {
    "noEmit": true // no output is required
  },
  "include": ["./src/**/*.ts"]
}

```

- `tsconfig.build.json`

```json
// this tsconfig is used for transpile the code when building
{
  "extends": "tsconfig.base.json",
  "compilerOptions": {
    "outDir": "dist",
    "noEmitOnError": true // don't transpile the code if there's an error
  },
  "include": ["./src/**/*.ts"],
  "exclude": ["./src/**/*.test.ts"]
}
```

Update `package.json`.

```json
{
  // ---
  "scripts": {
    //"build": "rimraf dist && tsc --project tsconfig.json",
    "build": "rimraf dist && tsc --project tsconfig.build.json",
  }
  // ---
}
```




