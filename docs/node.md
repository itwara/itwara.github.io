# node

## mjs
    Node.js >= v13

    It's very simple in Node.js 13 and above. You need to either:

    Save the file with .mjs extension, or
    Add { "type": "module" } in the nearest package.json.
    You only need to do one of the above to be able to use ECMAScript modules.

    Node.js <= v12

    If you are using Node.js version 9.6 - 12, save the file with ES6 modules with .mjs extension and run it like:

    node --experimental-modules my-app.mjs