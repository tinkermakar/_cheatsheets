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


## Array methods

1. Most used ones: `array.find` & `array.filter`

1. Check if a variable is an Array
    ```js
    const isArray = array instanceof Array;
    # or
    const isArray = Array.isArray(value)
    ```

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
    const isMatchingAll = array.every(el => el.name)
    ```

1. Crete an array (just as an iterable) with any length necessary
    ```js
    new Array(5).fill(0)
    ```

1. group array elements by a matching property value
    ```js
    const arr= [{ id: 1, balance: 1 }, { id: 2, balance: 2 }, { id: 3, balance: 1 }];

    Object.groupBy(arr, ({balance}) => balance);
    // { '1': [ { id: 1, balance: 1 }, { id: 3, balance: 1 } ], '2': [ { id: 2, balance: 2 } ] }
    ```


## Arrow functions
1. Return an object from arrow function
    ```js
    const function1 = () => ({ key1: value1, key2: value2 });
    ```

1. To return a multi-line statement from an <em>arrow function</em>, it’s necessary to use `()` instead of `{}` to wrap your function body. This ensures the code is evaluated as a single statement.

## Destructuring

1. Remove one or more known fields while keeping a clean copy of the remaining object:
    ```js
    const { password, ...safeUser } = user;
    ```

1. Pull a property whose name is only known at runtime:
    ```js
    const { [propertyName]: value } = user;
    ```

## Using Debuggers

1. Add this to launch.json to preserve Chrome state across debug sessions in terms of settings and Chrome plugins:
    ```json
    {
      ...
      "configurations": [
      {
        ...
        "runtimeArgs": [
            "--user-data-dir=${env:HOME}/chrome-debug-profile"
        ]
      }
    }
    ```

1. Call stack is debugging's backwards time machine

1. Right click on the gutter (line numbers) to add an additional condition to the breakpoint

1. VScode right click on a breakpoint and press log message (instead of console logging)

1. In Chrome DevTools I can right click anywhere in a file (jQuery Library, Node.js module file) and blackbox it so as I would never get into them when debugging

## Node Packages

1. Use `npm ci` instead of `npm install` in CI/CD and deployments for a clean, reproducible install from the lockfile.

1. For private GitHub Packages, use a personal access token with only the required package-read permission.

1. Reduce exposure to npm supply-chain attacks by refusing package versions published less than 7 days ago. Add this to the project's `.npmrc`:
    ```ini
    min-release-age=7
    ```

    If a newly published version fixes a vulnerability in the news but it's fresher than 7 days:
    ```bash
    npm audit fix --min-release-age-exclude=one-specific-package

    # Or a more permissive
    npm audit fix --min-release-age=0
    ```

1. Apache replacement: `http-server`

1. Logging: `log4js`

1. Security:
    - Validate and sanitize strings: `validator`
    - Validate incoming HTTP request body, params etc: `joi`
    - Secure HTTP headers in express.js: `helmet`
    - Hash/Encrypt-decrypt: `crypto` or `bcrypt`
    - Use `express-rate-limit` to prevent DDOS attacks 
    - Easy sanitization:
        ```js
        data.toString().trim();
        ```

1. Unit tests:
    - mock MongoDB: `sinon`
    - test express.js without starting it: `supertest`
    - BONUS terminology: two main types of `test doubles` used in unit/integration tests are `test stubs` and `mocks`.

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

1. `structuredClone` instead of `JSON.parse(JSON.stringify(object))`.

1. Check for real errors with `Error.isError(e)`

1. Bind (TODO make a separate section about it?)
    `function.bind` does not run the function, but it can also pre-define first parameter(s):
    ```js
    const foo = bar.bind(this, setValue)
    ```

1. <em>Operator Precedence</em> in JavaScript makes multiplication (`x`) run before `+`

1. Don't forget to encode and decode query parameters with `encodeURIComponent()` and `decodeURIComponent()`

1. `URLSearchParams` and `URL` are useful to construct and pars URLs and query params

1. Use `AbortController` to cancel fetches and clean up event listeners with one signal. (credit: https://dev.to/sylwia-lask/stop-installing-libraries-10-browser-apis-that-already-solve-your-problems-35bi)

1. Server-Sent Events are a simpler real-time option than WebSockets when the flow is only server-to-client.

1. Padding strings is now built-in
    ```js
    String(7).padStart(3, '0')
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

1. a shorthand for `filter().map()`
    credit: https://dev.to/rajajaganathan/flatmap-vs-filtermap-code-simplicity-aeb
    ```js
        const arr = [{foo: null}, {foo: undefined}, {foo: 0}, {foo: 1}, {foo: 2}];
        arr.flatMap(({ foo }) => foo ? foo : []);
    ```

1. An alternative to `console.time()`
    ```js
    const {performance} = require('node:perf_hooks');
    const start = performance.now();
    const end = performance.now();
    const diff = end - start;
    ```
