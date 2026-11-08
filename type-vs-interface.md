# Type Aliases vs Interfaces in TypeScript

## Introduction

TypeScript provides both `type` aliases and `interface` declarations for describing the shape of data. They often look similar, but they offer different capabilities. Choosing the right one makes a codebase easier to understand and maintain.

## Detailed Discussion

An interface is commonly used to describe the structure of objects and class contracts. Interfaces can be extended with `extends`, and declarations with the same name can merge.

```ts
interface Person {
  name: string;
}

interface Employee extends Person {
  employeeId: number;
}
```

A type alias can describe an object too, but it can also represent unions, intersections, tuples, and primitive aliases.

```ts
type Status = "pending" | "approved" | "rejected";

type User = {
  id: number;
  name: string;
};

type Admin = User & {
  permissions: string[];
};
```

The key practical difference is that interfaces support declaration merging, while type aliases do not. For example, a second declaration of `Person` can add another property to the interface. A type alias with the same name cannot be redeclared.

Both can describe object shapes and both can be extended in appropriate ways. Therefore, the choice is not about one being universally better. Use an interface when defining object contracts, public APIs, or class-oriented structures that may be extended. Use a type alias when representing unions, tuples, intersections, or when a named type expression is useful.

## Conclusion

Interfaces are a natural choice for extensible object contracts. Type aliases are more flexible for complex type expressions. Consistent use within a project is more important than treating either feature as the only correct option.
