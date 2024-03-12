# HTML Cheatsheet

1. `<script defer ...>` runs the script only when the page is done loading

1. Preload resources with pure HTML
    ```html
    <head>
      <link rel="preload" href="example.jpg" as="image" />
    ```

1. Lazy load images
    ```html
    <img src="/icon.png" loading="lazy" />
    ```

1. How to escape HTML markup
    ```html
    <![CDATA[<sender>John Smith</sender>]]>
    ```
    the above outputs the below
    ```
    &lt;sender&gt;John Smith&lt;/sender&gt;
    ```

1. Do not use `<b>` and `<i>`, use `<em>` and `<strong>`

1. use `<mark>` to highlight text with a yellow marker

1. Don't use `<ul>/<li>` for two column lists, use [Description Lists](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/dl):

1. `<datalist>` is a select with built-in autosuggest

1. Define multiple image sizes for all screen resolutions with `<picture>`

1. Talking to robots
    ```html
    <!-- point at the original source of this page's content -->
    <link rel="canonical" ... />

    <!-- indexing instructions for robots (skip etc.) -->
    <meta name="robots" ... />
    ```