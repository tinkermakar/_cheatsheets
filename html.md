# HTML Cheatsheet

1. `<script defer ...>` runs the script only when the page is done loading

1. How to escape HTML markup
    ```
    <![CDATA[<sender>John Smith</sender>]]>
    ```
    the above outputs the below
    ```
    &lt;sender&gt;John Smith&lt;/sender&gt;
    ```

1. Do not use `<b>` and `<i>`, use `<em>` and `<strong>`

1. use `<mark>` to highlight text with a yellow marker

1. Don't use `<ul>/<li>` for two column lists, use [Description Lists](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/dl):
