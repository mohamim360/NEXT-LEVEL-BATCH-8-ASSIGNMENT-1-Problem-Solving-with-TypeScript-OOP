# Type vs Interface in TypeScript: What Is the Difference?

## Introduction

In TypeScript, `type` and `interface` seem almost the same. Both can describe the shape of an object but choosing between them can feel confusing. The difference becomes clearer when we look at what each one can represent and how it can be extended.

## Main Differences

An `interface` is an object's structure. For example:

```ts
interface User {
  id: number;
  name: string;
}
```

A `type` alias can be the same object, but it can also represent other kinds of types, such as unions and tuples:

```ts
type UserAlias = { id: number; name: string };
type Status = "pending" | "active" | "blocked";
type Coordinates = [number, number];
```

Another difference is that interfaces support declaration merging. If I declare the same interface name more than once, TypeScript combines its members. A type alias cannot be declared again with the same name.

Both can be extended. An interface uses extends, while a type alias commonly uses an intersection (&):

```ts
interface Admin extends User {
  role: "admin";
}

type AdminUser = User & { role: "admin" };
```

Classes can also implement either an interface or an object-shaped type.

## Conclusion

Interface chosen for clear object contracts, when other parts of the project may need to extend them. I choose type when I need unions, tuples, or type combinations. For a simple object shape, either works but consistency across the project matters more than picking a winner.
