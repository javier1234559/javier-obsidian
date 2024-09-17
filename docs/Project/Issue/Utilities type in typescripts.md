---
Created: 12:33 17-09-2024
tags:
  - issue
---

TypeScript provides several built-in utility types that allow you to manipulate and transform types. Here’s a list of the most commonly used TypeScript utility types:

### 1. **`Partial<Type>`**
   - Constructs a type where all properties of `Type` are optional.
   - Example:
     ```typescript
     interface User {
       name: string;
       age: number;
     }
     const partialUser: Partial<User> = { name: "John" }; // 'age' is optional
     ```

### 2. **`Required<Type>`**
   - Constructs a type where all properties of `Type` are required.
   - Example:
     ```typescript
     interface User {
       name?: string;
       age?: number;
     }
     const requiredUser: Required<User> = { name: "John", age: 25 }; // all properties are required
     ```

### 3. **`Readonly<Type>`**
   - Constructs a type with all properties of `Type` set to `readonly`, preventing reassignment.
   - Example:
     ```typescript
     interface User {
       name: string;
       age: number;
     }
     const readonlyUser: Readonly<User> = { name: "John", age: 25 };
     readonlyUser.name = "Doe"; // Error: cannot assign to 'name' because it is a read-only property
     ```

### 4. **`Record<Keys, Type>`**
   - Constructs an object type where the keys are `Keys` and the values are `Type`.
   - Example:
     ```typescript
     type Role = "admin" | "user";
     const roles: Record<Role, string> = {
       admin: "John",
       user: "Jane"
     };
     ```

### 5. **`Pick<Type, Keys>`**
   - Constructs a type by picking the specified `Keys` from `Type`.
   - Example:
     ```typescript
     interface User {
       name: string;
       age: number;
       address: string;
     }
     const userWithAddress: Pick<User, "name" | "address"> = { name: "John", address: "123 Street" };
     ```

### 6. **`Omit<Type, Keys>`**
   - Constructs a type by omitting the specified `Keys` from `Type`.
   - Example:
     ```typescript
     interface User {
       name: string;
       age: number;
       address: string;
     }
     const userWithoutAge: Omit<User, "age"> = { name: "John", address: "123 Street" };
     ```

### 7. **`Exclude<Type, ExcludedUnion>`**
   - Constructs a type by excluding from `Type` all union members that are assignable to `ExcludedUnion`.
   - Example:
     ```typescript
     type T = Exclude<"a" | "b" | "c", "a">; // Result: "b" | "c"
     ```

### 8. **`Extract<Type, Union>`**
   - Constructs a type by extracting from `Type` all union members that are assignable to `Union`.
   - Example:
     ```typescript
     type T = Extract<"a" | "b" | "c", "a" | "c">; // Result: "a" | "c"
     ```

### 9. **`NonNullable<Type>`**
   - Constructs a type by excluding `null` and `undefined` from `Type`.
   - Example:
     ```typescript
     type T = NonNullable<string | number | undefined>; // Result: string | number
     ```

### 10. **`ReturnType<Type>`**
   - Constructs a type consisting of the return type of function `Type`.
   - Example:
     ```typescript
     function getUser() {
       return { name: "John", age: 25 };
     }
     type UserReturnType = ReturnType<typeof getUser>; // Result: { name: string, age: number }
     ```

### 11. **`InstanceType<Type>`**
   - Constructs a type consisting of the instance type of a constructor function `Type`.
   - Example:
     ```typescript
     class User {
       name = "John";
       age = 25;
     }
     type UserInstanceType = InstanceType<typeof User>; // Result: User
     ```

### 12. **`Parameters<Type>`**
   - Constructs a tuple type consisting of the types of the parameters of function `Type`.
   - Example:
     ```typescript
     function getUser(name: string, age: number) { }
     type Params = Parameters<typeof getUser>; // Result: [string, number]
     ```

### 13. **`ConstructorParameters<Type>`**
   - Constructs a tuple or array type of all the parameters of a constructor function `Type`.
   - Example:
     ```typescript
     class User {
       constructor(public name: string, public age: number) {}
     }
     type UserConstructorParams = ConstructorParameters<typeof User>; // Result: [string, number]
     ```

### 14. **`ThisParameterType<Type>`**
   - Extracts the type of `this` parameter from a function type, or `unknown` if the function does not have a `this` parameter.
   - Example:
     ```typescript
     function sayHello(this: User) {
       console.log(this.name);
     }
     type ThisType = ThisParameterType<typeof sayHello>; // Result: User
     ```

### 15. **`OmitThisParameter<Type>`**
   - Removes the `this` parameter from a function type.
   - Example:
     ```typescript
     function sayHello(this: User) {
       console.log(this.name);
     }
     const newFunc: OmitThisParameter<typeof sayHello> = () => { console.log('No this') };
     ```

### 16. **`Awaited<Type>`**
   - Used to get the type of the value inside a `Promise`.
   - Example:
     ```typescript
     type AwaitedResult = Awaited<Promise<string>>; // Result: string
     ```

These utility types are extremely helpful for transforming and working with existing types in a more flexible way. Let me know if you need any specific examples or further explanations!