# TypeScript Cheatsheet

1. use `never` isntead of `unknown` whenever possible

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

1. Utilities:
    1. `Required<...>` is the opposite of `Partial<...>`
    1. `Omit<...>` is the opposite of `Pick<...>`
    1. `Exclude<...>` is the opposite of `Extract<...>` and they are a similar to what `Pick` and `Omit` do, but for Union types, not objects.

    1. More great utilities here: https://dev.to/bhataasim/advanced-typescript-utility-types-in-detail-4mdh


