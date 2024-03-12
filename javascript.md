# JavaScript Cheatsheet

## Loops

1. Loop through array items
    ```js
    for (let el of arr) {}
    ```

1. Loop through array or object keys
    ```js
    for (let el in arr) {}
    ```


## Break out of a loop

1. Jump <em>out</em> of a loop: `break`
1. Jump <em>over</em> one iteration in the loop: `continue`


## Prototypes

- Old school: `const Object = new Prototype()`
- ES6 onwards: `Object extends Prototype()`


## Arrow functions

1. Most used ones: `array.find` & `array.filter`

1. Check if a variable is an Array
    ```js
    const isArray = array instanceof Array;
    ```

1. Return an object from arrow function
    ```js
    const function = () => ({ key1: value1, key2: value2 });
    ```

1. To return a multi-line statement from an <em>arrow function</em>, it’s necessary to use `()` instead of `{}` to wrap your function body. This ensures the code is evaluated as a single statement.

1. Check if array includes a certain value among entries
    
    - If simple check
        ```js
        array.includes('string');
        ```

    - If more complex expression is needed
        ```js
        const isIncluded = array.some(el => el.name === 'example');

        // or for negative check
        const isNotIncluded = !array.some(cb)
        ```

1. Check if all entries of an array match an expression (returns true if all elements returned true)

    ```js
    const isMatchingAll = array.some(el => el.name)
    ```


## Using Debuggers

1. Call stack is debugging's backwards time machine

1. Right click on the gutter (line numbers) to add an additional condition to the breakpoint

1. VScode right click on a breakpoint and press log message (instead of console logging)

1. In Chrome DevTools I can right click anywhere in a file (jQuery Library, Node.js module file) and blackbox it so as I would never get into them when debugging


## Node Packages

1. Apache replacement: `http-server`

1. Logging: `log4js`

1. Security:
    - Validate and sanitize strings: `validator`
    - Validate incoming HTTP request body, params etc: `joi`
    - Secure HTTP headers in express.js: `helmet`
    - Encrypt-decrypt: `crypto` or `bcrypt`
    - Use `express-rate-limit` to prevent DDOS attacks 
    - Easy sanitization:
        ```js
        data.toString().trim();
        ```


## Misc

1. Fallback value
    ```js
    const foo = bar ?? 111;
    // or
    const foo = bar || 111;
    ```
    
    The difference -- when using `||` all these falsy values result in the return of the fallback value: `0, '', NaN, null, undefined`. However, `??` only takes the fallback value only if the first is  `null` or `undefined`. This is helpful to avoid from skipping `0` or an empty string when they are actually legit values.  

1. Conditional object fields
    ```js
    const obj = {
        a: 1,
        b: 2,
        ...(foo && { foo: 'bar'})
    }
    ```

1. Bind (TODO make a separate section about it?)
    `function.bind` does not run the function, but it can also pre-define first parameter(s):
    ```js
    const foo = bar.bind(this, setValue)
    ```

1. <em>Operator Precedence</em> in JavaScript makes multiplication (`x`) run before `+`

1. Don't forget to encode and decode query parameters with `encodeURIComponent()` and `decodeURIComponent()`

1. `URLSearchParams` and `URL` are useful to construct and pars URLs and query params

1. Padding strings is now built-in
    ```js
    7.padStart(3, '0')
    // '007'
    ```

1. Smooth scroll
    ```js
    document.querySelector(element).scrollIntoView({  behavior: 'smooth' });
    ```

1. Reverse `Object.entries` with `Object.fromEntries()`

1. Browsers have built-in TTS now
    ```js
    let utterance = new SpeechSynthesisUtterance("Hello world!");
    speechSynthesis.speak(utterance);
    ```
