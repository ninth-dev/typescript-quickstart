## Prettier

```sh
yarn add --dev prettier
```

## Prettier Config

```sh
cat << EOF > .prettierrc
{
  "printWidth": 120
}
EOF
```

Add some scripts in `package.json`:

```json
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

```js
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

Setting up your editor to auto-format.....

https://prettier.io/docs/en/editors.html
