# Accessibility Cheatsheet

1. Form buttons need descriptive, human-readable text. For `<input type="submit">`, `<input type="button">`, and `<input type="reset">`, set `value` to the action, such as “Save changes”, not `save-changes` or `saveChanges`. For `<button>`, the text inside the element supplies its name; its `value` is form data and may use an internal identifier. No `aria-label` is needed when this text already names the button. See [WAI button naming](https://www.w3.org/WAI/WCAG21/Techniques/html/H91.html).

    ```html
    <input type="submit" value="Save changes" />
    <button type="submit" name="action" value="saveChanges">Save changes</button>
    ```

1. Icon-only button/link with no accessible name from its content: provide one with `aria-label` or visually hidden text.

    ```html
    <button type="button" aria-label="Close dialog">
      <span aria-hidden="true">×</span>
    </button>
    ```

1. Dialogs need an accessible name: a heading inside `<dialog>` does not automatically name it. Use `aria-labelledby` referencing the heading's unique ID, or `aria-label` when there is no visible title. See [WAI accessible names](https://www.w3.org/WAI/ARIA/apg/practices/names-and-descriptions/).

    ```html
    <dialog aria-labelledby="settings-title">
      <h2 id="settings-title">Settings</h2>
      <!-- Dialog contents -->
    </dialog>
    ```

1. Accessible names are very desired on  `<section>` and `<article>` elements. Prefer `aria-labelledby` referencing an existing heading; otherwise, `aria-label` supplies the name directly. See [WAI naming guidance](https://www.w3.org/WAI/ARIA/apg/practices/names-and-descriptions/).

1. Text inside an image counts as a visible label too. If a button/link's image says “Start free trial”, its accessible name must include that same wording, preferably at the beginning. See [WCAG Label in Name](https://www.w3.org/WAI/WCAG22/Understanding/label-in-name.html).


1. When an image supplies a button's or link's accessible name, its `alt` must describe the action or destination, not the image's appearance. See [functional images](https://www.w3.org/WAI/tutorials/images/functional/).

1. Use `alt=""` for decorative images or images.

1. “Skip to main content” (as well as other skip destinations when useful) lets keyboard users bypass repeated headers/navigation. Place it before other interactive elements so the first Tab within the page reveals it. Hide it visually until `:focus`. See [WAI skip-to-content guidance](https://www.w3.org/WAI/WCAG22/Techniques/general/G1.html).

    ```html
    <body>
      <a class="skip-link" href="#main-content">Skip to main content</a>
      <a class="skip-link" href="#search">Skip to search</a>

      <main id="main-content" tabindex="-1">
        <h1>Page title</h1>
      </main>
    ```

    ```css
    .skip-link {
      position: fixed;
      top: 1rem;
      left: 1rem;
      z-index: 1000;
      transform: translateY(calc(-100% - 2rem));
    }

    .skip-link:focus {
      transform: translateY(0);
    }
    ```
