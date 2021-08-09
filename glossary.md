## Glossary

## NVM

Node version manager, each project may use different version of Node. 
In Scala, `sbt` will manage this for us.

## Yarn

Yarn is a package manager.
- Alternatives are `npm`, `pnpm`.

This is similar to how use manage our dependencies with `sbt` in Scala.

### package.json

### What is the difference between `dependencies` and `dev-dependencies` ?

- Dependencies are what we need to run the code in production.
- Dev Dependencies are supporting dependencies to build / lint / test our code.


## TypeScript

- TypeScript is a superset of JavaScript.
- We will write in TypeScript, the code will be transpiled to pure JavaScript.

## Jest

- This is the current the most common test framework for JavaScript.
- We use `specs2` in Scala.

- However, to work with TypeScript - we will also need another library `ts-jest`

## ESLint

This is a code linter.

In Scala, it is similar to `wartremover`, `scalastyle`.

## Prettier

This is just a code formatter. However, it can format more than just `TypeScript`.

This works like `ScalaFmt` for Scala.

