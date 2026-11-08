# Type Narrowing in TypeScript

## Introduction

A union type allows a variable to hold values from more than one type. Before using a value, TypeScript often needs proof of which member of the union is currently present. Type narrowing is the process of using checks in code to reduce a broad type to a more specific type.

## Detailed Examples

The `typeof` operator is useful for primitive values such as strings and numbers.

```ts
function describe(value: string | number): string {
  if (typeof value === "string") {
    return value.toUpperCase();
  }
  return value.toFixed(2);
}
```

Inside the first branch, TypeScript knows that `value` is a string. In the other branch, it is a number.

The `instanceof` operator checks whether an object was created from a particular class or constructor.

```ts
class Dog {
  bark(): string {
    return "Woof";
  }
}

function makeSound(animal: Dog | Date): string {
  if (animal instanceof Dog) {
    return animal.bark();
  }
  return animal.toISOString();
}
```

The `in` operator checks whether a property exists on an object. It is especially useful for distinguishing object types in a union.

```ts
type EmailUser = { email: string };
type PhoneUser = { phone: string };

function contact(user: EmailUser | PhoneUser): string {
  if ("email" in user) {
    return user.email;
  }
  return user.phone;
}
```

These checks are not merely runtime decisions; TypeScript uses them to understand which operations are safe in each branch. This reduces unsafe assumptions and avoids unnecessary type assertions.

## Conclusion

Type narrowing makes union types practical and safe. Use `typeof` for primitive values, `instanceof` for class instances, and `in` to check object properties. These techniques help the compiler verify that code uses values correctly.
