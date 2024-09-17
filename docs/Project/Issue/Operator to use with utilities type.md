---
Created: 12:42 17-09-2024
tags:
  - issue
---
Link relates :
- [[Utilities type in typescripts]]

---

In TypeScript, you can use several operators along with utility types to create more advanced and flexible types. Some commonly used operators and techniques include `&` (intersection), `|` (union), `typeof`, `keyof`, and indexing types. Let’s break them down and how you can use them with utility types.

### 1. **Intersection (`&`)**
   - The `&` operator is used to create an intersection of types, meaning a type that has all properties of both types.
   - Example (like the one you provided):
     ```typescript
     export type IPropetyForm = Omit<
       PropertiesEntity, 
       "id" | "createdAt" | "updatedAt" | "owner" | "tenant" | "createdBy"
     > & { password: string };
     ```
   - **Explanation**: This creates a new type that combines the properties of the `Omit` type and the additional `{ password: string }` field.

### 2. **Union (`|`)**
   - The `|` operator is used to create a union of types, where a value can be of **either** type in the union.
   - Example:
     ```typescript
     type BasicInfo = { name: string };
     type AddressInfo = { address: string };

     type UserInfo = BasicInfo | AddressInfo;
     ```
   - **Explanation**: `UserInfo` can be either `{ name: string }` or `{ address: string }`. This allows more flexibility in what values the type can take.

### 3. **`typeof` Operator**
   - `typeof` allows you to extract the type of a variable, function, or class in TypeScript.
   - You often use it when you want to derive the type from a constant or a class.
   - Example:
     ```typescript
     const defaultFormValues = {
       name: "",
       area: null,
     };

     type DefaultFormValues = typeof defaultFormValues; // { name: string, area: null }
     ```
   - **Explanation**: `typeof` extracts the type from the variable `defaultFormValues`.

### 4. **`keyof` Operator**
   - `keyof` is used to get the **union of keys** from an object type.
   - Example:
     ```typescript
     interface PropertiesEntity {
       id: string;
       name: string;
       area: string;
     }

     type PropertyKeys = keyof PropertiesEntity; // "id" | "name" | "area"
     ```
   - **Explanation**: `keyof PropertiesEntity` gives you a union of the keys `"id" | "name" | "area"`.

### 5. **Indexing Types**
   - You can access a type’s property using indexing `[]` notation, allowing for type-safe lookups of property types.
   - Example:
     ```typescript
     interface PropertiesEntity {
       id: string;
       name: string;
       area: string;
     }

     type PropertyNameType = PropertiesEntity["name"]; // string
     ```
   - **Explanation**: `PropertiesEntity["name"]` gives the type of the `name` property, which is `string`.

### 6. **`in` Operator (Mapped Types)**
   - The `in` operator is used inside **mapped types**, where you can iterate over the keys of a type to transform it.
   - Example:
     ```typescript
     type OptionalProperties<T> = {
       [K in keyof T]?: T[K];
     };
     
     type OptionalPropertiesEntity = OptionalProperties<PropertiesEntity>;
     ```
   - **Explanation**: This creates a type where all properties of `PropertiesEntity` are optional.

### Putting It All Together:
You can combine multiple operators and utility types for more complex transformations:

#### Example: Creating a Partial Form with Required `password`
```typescript
type IPropetyForm = Omit<
  PropertiesEntity, 
  "id" | "createdAt" | "updatedAt" | "owner" | "tenant" | "createdBy"
> & { password: string };

// Let's say we want to make all properties optional except `password`
type OptionalFormWithRequiredPassword = Partial<IPropetyForm> & { password: string };
```

#### Example: Dynamically Enforcing Certain Fields
```typescript
type RequireSomeFields<T, K extends keyof T> = Omit<T, K> & Required<Pick<T, K>>;

type IPropetyFormWithRequiredName = RequireSomeFields<IPropetyForm, "name">;
```
- **Explanation**: This makes the `name` field required in `IPropetyForm`, while all other fields remain as defined.

### Summary of TypeScript Operators with Utility Types:
- **`&`**: Intersection, combining multiple types.
- **`|`**: Union, allowing a value to be one of several types.
- **`typeof`**: Extracts a type from a value.
- **`keyof`**: Gets the union of keys from an object type.
- **Indexing Types (`[]`)**: Access a specific property’s type.
- **`in`**: Used in mapped types to transform or iterate over a type's properties.

These operators and utility types, when combined, give you a powerful way to manipulate and compose types in TypeScript. Let me know if you'd like to dive deeper into any specific part!