+++
title = "TypeScript Tips for Better Code"
date = 2024-03-15
summary = "Level up your TypeScript skills with these practical tips and patterns"
tags = ["typescript", "javascript", "programming"]
categories = ["Development"]
+++

TypeScript makes JavaScript development safer and more productive. Here are tips to use it effectively.

## Type Inference

Let TypeScript infer when possible:

```typescript
// TypeScript infers the type
const name = "John"; // string
const age = 30; // number
const isActive = true; // boolean

// Explicit when needed
const users: User[] = [];
```

## Union Types

Handle multiple possible types:

```typescript
function formatValue(value: string | number): string {
  if (typeof value === "number") {
    return value.toFixed(2);
  }
  return value;
}
```

## Type Guards

Narrow types safely:

```typescript
interface Bird {
  fly(): void;
}

interface Fish {
  swim(): void;
}

function isBird(animal: Bird | Fish): animal is Bird {
  return (animal as Bird).fly !== undefined;
}

function move(animal: Bird | Fish) {
  if (isBird(animal)) {
    animal.fly();
  } else {
    animal.swim();
  }
}
```

## Utility Types

Use built-in utility types:

```typescript
interface User {
  id: number;
  name: string;
  email: string;
  age: number;
}

// Make all properties optional
type PartialUser = Partial<User>;

// Pick specific properties
type UserPreview = Pick<User, 'id' | 'name'>;

// Omit specific properties
type UserWithoutId = Omit<User, 'id'>;

// Make all properties readonly
type ReadonlyUser = Readonly<User>;
```

## Generics

Create reusable, type-safe code:

```typescript
function identity<T>(arg: T): T {
  return arg;
}

// Generic interface
interface Response<T> {
  data: T;
  status: number;
  message: string;
}

// Generic class
class Collection<T> {
  private items: T[] = [];
  
  add(item: T): void {
    this.items.push(item);
  }
  
  getAll(): T[] {
    return this.items;
  }
}
```

## String Literal Types

Create precise types:

```typescript
type Status = 'idle' | 'loading' | 'success' | 'error';
type HttpMethod = 'GET' | 'POST' | 'PUT' | 'DELETE';

function setStatus(status: Status) {
  // TypeScript ensures only valid values
}
```

## Mapped Types

Transform types:

```typescript
type Flags<T> = {
  [K in keyof T]: boolean;
};

interface User {
  name: string;
  email: string;
}

// Result: { name: boolean; email: boolean; }
type UserFlags = Flags<User>;
```

## Conditional Types

Types that depend on conditions:

```typescript
type IsString<T> = T extends string ? true : false;

type A = IsString<string>; // true
type B = IsString<number>; // false
```

## Const Assertions

Preserve literal types:

```typescript
// Regular object (mutable)
const config = {
  api: 'https://api.example.com',
  timeout: 5000
};

// With const assertion (immutable)
const config = {
  api: 'https://api.example.com',
  timeout: 5000
} as const;
```

## never Type

Represent impossible values:

```typescript
function error(message: string): never {
  throw new Error(message);
}

function assertNever(value: never): never {
  throw new Error(`Unexpected value: ${value}`);
}

// Exhaustive switch
type Shape = Circle | Square;

function area(shape: Shape): number {
  switch (shape.kind) {
    case 'circle':
      return Math.PI * shape.radius ** 2;
    case 'square':
      return shape.size ** 2;
    default:
      return assertNever(shape); // Ensures all cases handled
  }
}
```

## Best Practices

1. Enable strict mode
2. Avoid `any` type
3. Use `unknown` instead of `any`
4. Prefer interfaces over type aliases for objects
5. Use enums sparingly
6. Leverage type inference
7. Document complex types

TypeScript's type system is powerful. Master these patterns and write safer, more maintainable code.
