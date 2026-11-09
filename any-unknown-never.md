# Understanding `any`, `unknown`, and `never` in TypeScript

## Introduction

In TypeScript `any`, `unknown`, and `never` looked like three types that did the same thing. But they actually have very different jobs.

## How They Work

You can assign anything to `any` and call any property or method, even if that operation is wrong.

```ts
let data: any = "hello";
data.toFixed(); // TypeScript allows this, but it fails at runtime.
```

`unknown` can also hold a value of any type, but TypeScript does not let us use it until we check what it is. That extra step is useful when handling API responses or user input.

```ts
let data: unknown = "hello";

if (typeof data === "string") {
  console.log(data.toUpperCase()); // Safe after the check
}
```

`never` is used for values that should never exist. A function that always throws an error can have a `never` return type.

```ts
function fail(message: string): never {
  throw new Error(message);
}
```

`unknown`: sits at the top as the safest “I don’t know yet” type and every value can be assigned to it. 

`never`: sits at the bottom as the impossible type and It can be assigned to every type, but normally has no values. 

`any`: is special because it largely bypasses these safety rules. Also for migration like when converting a large JavaScript codebase to TypeScript, it lets developers get out of type checking file by file without breaking everything at once.

## Conclusion

I do prefer `unknown` over `any` when the type is not known yet. It makes me check the value before using it, which prevents many avoidable runtime errors. Use `any` only when get out of type checking is intentional, and use `never` when a value should be impossible.
