## Prettier

```sh
yarn add --dev prettier
```

## Prettier Config

NB: Prettier recommends the `printWidth` of `80`. tl;dr Use what works for yourself or your team :)

```sh
cat << EOF > .prettierrc
{
  "printWidth": 120
}
EOF
```

Add some scripts in `package.json`:

```json5
{
  // ---
  "scripts": {
    //---
    "prettier:check": "prettier --check '**/*.ts'",
    "prettier:fix": "prettier --write '**/*.ts'",
  },
  // ---
}
```

Example:

```ts
const test = "Hello World";;
```

ESLint will complain, but Prettier can fix it.

```sh
yarn add --dev eslint-config-prettier
```

`eslint-config-prettier` - disable the eslint rules that will conflict or are unnecessary with Prettier.

```json5
{
// ---
"extends": [
  "eslint:recommended",
  "plugin:@typescript-eslint/recommended",
  "plugin:@typescript-eslint/recommended-requiring-type-checking",
  "prettier" // Add this config at the end of the extends
],
// ---
}
````

## Recommended

Setting up your editor to auto-format, this is just a recommedation and is optional. From experience I've found it to be quite useful!

https://prettier.io/docs/en/editors.html
