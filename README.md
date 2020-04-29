# typescript-utilities-guide

a list of typescript helper libraries. advanced guides in `typescript-cheatsheets` will assume knowledge of these and refer people here.

There is a stage in every TypeScript journey where you struggle getting the types you want and eventually find a lifesaver blogpost like [TypeScript Types You Should Know About](https://xpbytes.com/articles/types-you-should-know-about-typescript/). This cheatsheet accumulates them.

## Utility Types

Be familiar with the [Utility Types that ship with TS](https://www.typescriptlang.org/docs/handbook/utility-types.html). On top of that, here are handy Utility Types often used by TS practitioners, with explanation on what they do and how they can help. We will assume knowledge of [mapped types and conditional types](https://mariusschulz.com/blog/series/typescript-evolution) like `Exclude<T, U>` and `ReturnType<T>` but try to build progressively upon them.

> Note: If you are new to conditional types, I highly recommend [DJSheldrick's blogpost and talk on Conditional Types in TypeScript](https://artsy.github.io/blog/2018/11/21/conditional-types-in-typescript/)

<details>
  <summary>
    <code>Optionalize&lt;T extends K, K&gt;</code>: Remove from T the keys that are in common with K
  </summary>
  
```ts
/**
 * Remove from T the keys that are in common with K
 */
type Optionalize<T extends K, K> = Omit<T, keyof K>;
```
  
  An example usage is in our HOC section below.
  
</details>
<details>
  <summary>
    <code>Nullable&lt;T&gt;</code> or <code>Maybe&lt;T&gt;</code>: Make a Type into a Maybe Type
  </summary>
  
```ts
/**
 * Make a Type into a Maybe Type
 */
type Nullable<T> = T | null
type Maybe<T> = T | undefined
```

Your choice of `null` or `undefined` depends on your approach toward missing values. Some folks feel strongly one way or the other.

</details>
<details>
  <summary>
    <code>Dictionary&lt;T&gt;</code>: Dictionary of string, value pairs
  </summary>
  
```ts
/**
 * Dictionary of string, value pairs
 */
type Dictionary<T> = { [key: string]: T }
```

`[key: string]` is a very handy trick in general. You can also modify dictionary fields with [Readonly](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-2-8.html) or make them optional or Omit them, etc.

</details>

There also exist helper type libraries:

- [utility-types](https://github.com/piotrwitek/utility-types)
- [type-zoo](https://github.com/pelotom/type-zoo)
- [typesafe-actions](https://github.com/piotrwitek/typesafe-actions)
- [type-fest](https://github.com/sindresorhus/type-fest)
- [tsdef](https://github.com/joonhocho/tsdef)
- [rex-tils](https://github.com/Hotell/rex-tils)
- [ts-toolbelt](https://github.com/pirix-gh/ts-toolbelt) ([Reddit](https://www.reddit.com/r/typescript/comments/c2nq7k/higher_type_safety_for_typescript_with_tstoolbelt/))
- [tiny-types](https://github.com/jan-molak/tiny-types)

seriously, check some of these out, they represent a ton of accumulated typescript experience.

## Type Testing

- https://github.com/SamVerschueren/tsd: Check TypeScript type definitions
- https://github.com/aikoven/typings-tester#readme
- https://github.com/ikatyang/dts-jest
- https://github.com/SamVerschueren/tsd
- https://github.com/azz/jest-runner-tsc
- https://github.com/microsoft/dtslint ([Intro to dtslint](https://www.youtube.com/watch?v=nygcFEwOG8w&feature=share))

## TypeScript Plugins

You can write plugins to modify typescript syntax itself. this is ADVANCED and not exactly recommended but here are some examples if you need them:

- https://github.com/rimeto/ts-optchain/

## Misc

- https://github.com/urish/typewiz Automatically discover and add missing types in your TypeScript code
- https://github.com/microsoft/rushstack/tree/master/apps/api-extractor

API Extractor provides an integrated, professional-quality solution for all these problems. It is invoked at build time by your toolchain and leverages the TypeScript compiler engine to:

- Detect a project's exported API surface
- Capture the contracts in a concise report designed to facilitate review
- Warn about common mistakes (e.g. missing exports, inconsistent visibility, etc.)
- Generate \*.d.ts rollups with trimming according to release type
- Output API documentation in a portable format that's easy to integrate with your content pipeline

## Codegen from TypeScript

- https://github.com/yousefed/typescript-json-schema
- https://github.com/apollographql/apollo-tooling/tree/master/packages/apollo-codegen-typescript

## Data Structures

https://github.com/basarat/typescript-collections
