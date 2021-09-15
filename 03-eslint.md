## Setting up ESLint

```
yarn add --dev eslint
yarn add --dev @typescript-eslint/eslint-plugin @typescript-eslint/parser
```

https://github.com/typescript-eslint/typescript-eslint/blob/master/docs/getting-started/linting/README.md#configuration

```
yarn eslint --init
```

```sh
cat <<EOF > .eslintrc.js
module.exports = {
  root: true,
  extends: [
    "eslint:recommended",
    "plugin:@typescript-eslint/recommended",
    "plugin:@typescript-eslint/recommended-requiring-type-checking", // if too slow, spilt this out.
  ],
  parser: "@typescript-eslint/parser",
  parserOptions: {
    ecmaVersion: 12,
    sourceType: "module",
    tsconfigRootDir: __dirname,
    project: ['./tsconfig.json']
  },
  plugins: [
    "@typescript-eslint"
  ],
  rules: {
    "@typescript-eslint/no-unused-vars": ["error", { argsIgnorePattern: "^_" }]
  }
};
EOF
```

https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin/docs/rules


## Gotchas!

You don't need to specify the `env` in the eslint config.
It is usually used when you are using the rule [`no-undef`](https://eslint.org/docs/rules/no-undef)
However, we are using [`plugin:@typescript-eslint/recommended`](https://github.com/typescript-eslint/typescript-eslint/blob/master/packages/eslint-plugin/src/configs/eslint-recommended.ts#L24),
the rule is disabled.

The `tsconfig.json` already specifies something similar (https://www.typescriptlang.org/tsconfig#target) and types.


Create `.eslintignore`

```sh
echo "dist" > .eslintignore
```

Add scripts to `package.json`

```json5
{
  // ---
  "scripts": {
    //---
    "lint": "eslint . --ext .ts",
    "lint:fix": "eslint . --ext .ts --fix",
  },
  // ---
}
```

## Other eslint plugins

### [eslint-plugin-import](https://github.com/import-js/eslint-plugin-import)

`yarn add --dev eslint-plugin-import`

```js
{
  // ---
  extends: [
    // ---
    "plugin:import/recommended",
    "plugin:import/typescript"
    // ---
  ],
  // ---
  plugins: [
    // ---
    "import"
    // ---
  ]
}
```

## [eslint-plugin-jest](https://www.npmjs.com/package/eslint-plugin-jest)

```
yarn add --dev eslint eslint-plugin-jest
```

## [eslint-plugin-fp]()

## [eslint-plugin-fp-ts](https://www.npmjs.com/package/eslint-plugin-fp-ts)





