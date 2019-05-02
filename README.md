# typescript-utilities-guide

a list of typescript helper libraries. advanced guides in `typescript-cheatsheets` will assume knowledge of these and refer people here.

## Utility Types

Be familiar with the [Utility Types that ship with TS](https://codewithstyle.info/Comprehensive-list-of-useful-built-in-types-in-TypeScript/). On top of that, here are handy Utility Types often used by TS practitioners, with explanation on what they do and how they can help. We will assume knowledge of [mapped types and conditional types](https://mariusschulz.com/blog/series/typescript-evolution) like `Exclude<T, U>` and `ReturnType<T>` but try to build progressively upon them.

<details>
  <summary>
    <code>Omit&lt;T, K extends keyof T&gt;</code>: Subtract keys from one interface from the other.
  </summary>
  
```ts
/**
 * Subtract keys from one interface from the other.
 *
 * @example
 * interface One { one: string }
 * interface Three { one: string, two: string }
 *
 * type Two = Omit<Three, keyof One>;
 *
 * // The type of Two will be
 * interface Two { two: string }
 */
type Omit<T, K extends keyof T> = Pick<T, Exclude<keyof T, K>>;
```

You can also supply string literals to omit:

```ts
type SettingsPageProps = Omit<
  ServerConfig,
  'immutableSetting1' | 'invisibleSetting2'
>;
```

</details>

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

## Misc

- https://github.com/urish/typewiz Automatically discover and add missing types in your TypeScript code

## Codegen from TypeScript

- https://github.com/yousefed/typescript-json-schema
- https://github.com/apollographql/apollo-tooling/tree/master/packages/apollo-codegen-typescript


## Data Structures

https://github.com/basarat/typescript-collections
