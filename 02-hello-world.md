# Hello World

## File structure

```sh
|- dist # output of the file - configurable in tsconfig
|- src # where all the code sits - configurable in tsconfig
|   |- index.ts
|   |- __tests__
|       |- index.test.ts
|- node_modules # this where the dependency are pulled into, you don't need to commit this.
|- tsconfig.json # typescript compiler config
|- package.json # scripts and dependencies are listed here
|- yarn.lock
|- .nvmrc # version of node
|- .npmrc # ???
|- .eslintrc.js
|- .prettierrc
|- jest.config.js
```

## Start project

```sh
mkdir -p typescript-hello-world/src
cd typescript-hello-world
yarn init
cat package.json
```

### Add TypeScript

```sh
yarn add --dev typescript
yarn add --dev @types/node # all typings for node
yarn add --dev @tsconfig/node14 # recommend settings if we know what version of node we are targetting.
```

These are all `dev-dependencies`.
Once our code has transpiled to JavaScript, these dependencies are not required to run.

### Setup tsconfig.json

```sh
cat << EOF > tsconfig.json
{
  "extends": "@tsconfig/node14/tsconfig.json"
  "compilerOptions": {
    "outDir": "dist",
    "noEmitOnError": true // don't transpile the code if there's an error
  },
  "include": [
    "./src/**/*.ts"
  ]
}
EOF
```

### Hello world

Within `src`, create `index.ts` with :

```ts
console.log("Hello World!");
```

### rimraf

Just think of this as just `rm -f` but will work in all operating system

```sh
yarn add --dev rimraf
```

### Create some scripts in package.json

```json
{
  // ---
  "scripts": {
    "build": "rimraf dist && tsc --project tsconfig.json",
    "start": "node dist/index.js"
  },
  // ---
}
```

### Run !

```sh
yarn install # or just yarn
yarn build
yarn start
```

### XXX

- `tsc --build` would like to understand this more.
