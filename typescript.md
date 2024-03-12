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

1. Make an object immutable
    ```ts
    const obj = {
      foo: 'bar'
    } as const
    ```

1. `Required<...>` is the opposite of `Partial<...>`

1. `protected` methods of TS classes are private, but accessible by child classes
