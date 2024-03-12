# CSS Cheatsheet

1. How to create light-grey, dark-grey, light-grey effect, like on a spreadsheet
    ```css
    :nth-child(odd) { ... }
    ```

1. Selects every `<a>` element whose href attribute value ends with `.pdf`
    ```css
    a[href$=".pdf"]
    ```

1. Nice slider: https://www.jssor.com/

1. `background` (NOT `background-image`) MUST come after `background-size`

1. css grid magic
    ```css
    grid-repeat-colums: repeat(auto-fit, minmax(19rem, 1fr));
    ```

1. Set Aspect ration with CSS -- with `aspect-ratio`

1. A built-in way to support dark theme
    ```css
    @media (prefers-color-scheme: dark)
    ```

1. Use `text-wrap: pretty` or `text-wrap: balance` on headings to wrap more than one word

1. Use multiple of the same CSS properties in reverse order to achieve fallback values in CSS

1. use `border-image` for fancy borders

1. CSS finally support selecting parents via child tags: `:has`

1. Extra conditional in CSS selectors can be defined with `:is()` and `:where()`. The only difference between the two is that specificity of `where` is flat 0
