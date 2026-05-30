# TypeScript Cheatsheet

1. use `never` instead of `unknown` whenever possible

1. Last resort pseudo-any types:
    ```ts
    export type EnumType = { [key: string]: string };
    export type ObjectType = { [key: string]: unknown | unknown[] };
    ```

1. An example of looping through an object's keys in the actual code:
    ```ts
    export const as = (table: string, sqlFields: EnumType, fields: EnumType) => {
      let output: string[] = [];

      for (const i in sqlFields) {
        const row = `${table}.${sqlFields[i]} as ${fields[i]}`;
        output.push(row);
      }
      return output;
    };
    ```

1. Make things immutable for TypeScript:
    1. make an object immutable by adding `as const` at the end of `const foo = { bar: 123 } as const`.
    1. make an object immutable by adding wrapping an interface declaration in `ReadOnly<>`.
    1. make an array immutable by adding wrapping an interface declaration in `ReadonlyArray<>`.
    1. make a field immutable by prefixing it with `readonly`.
    1. make a class property readonly by prefixing it with `readonly`.

1. `protected` methods of TS classes are private, but accessible by child classes

1. The correct way to declare private methods is not `private mtd` but `#mtd`.

1. Utilities:
    1. `Required<...>` is the opposite of `Partial<...>`
    1. `Omit<...>` is the opposite of `Pick<...>`
    1. `Exclude<...>` is the opposite of `Extract<...>` and they are a similar to what `Pick` and `Omit` do, but for Union types, not objects.

    1. More great utilities here: https://dev.to/bhataasim/advanced-typescript-utility-types-in-detail-4mdh

1. An alternative way to (not) use enums:
    ```ts
    const routes = { home: "/", admin: "/admin" } as const;
    type RouteName = keyof typeof routes; // "home" | "admin"
    ```

1. Get an array element type with `[number]`:
    ```ts
    const roles = ["admin", "editor"] as const;
    type Role = (typeof roles)[number]; // "admin" | "editor"
    ```

1. `infer` is used with `extends` to capture an inner part of a type that matches a pattern to pass on
    ```ts
    type GetReturnType<T> = T extends (...args: never[]) => infer Return ? Return : never;
    ```

1. Use `satisfies` to validate an object against a broad shape without losing the narrow inferred types of its values. (credit: https://dev.to/lingodotdev/beyond-the-basics-21-typescript-features-you-might-not-know-about-1dbn)
    ```ts
    const palette = {
      red: [255, 0, 0],
      green: "#00ff00",
    } satisfies Record<string, string | [number, number, number]>;
    ```
