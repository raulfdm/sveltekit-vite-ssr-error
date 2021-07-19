# Sveltekit + Vite: ReferenceError: module is not defined

This repository is meant to reproduce a problem when we add a dependency without the node builtins.

```
[vite] Error when evaluating SSR module /node_modules/is-buffer/index.js:
ReferenceError: module is not defined
    at /node_modules/is-buffer/index.js:8:1
    at instantiateModule (/Users/raul_personal/development/unified-sveltekit/node_modules/vite/dist/node/chunks/dep-11db14da.js:73323:166)
```

## Details

I'm currently trying to use `unified` (and later combine with `remark-parse`) to perform from some markdown string -> html client side, pretty much like [`react-markdown`](https://github.com/remarkjs/react-markdown) and many other library does.

However, when I try to import `unified` client side in Sveltekit it throws `ReferenceError: module is not defined`.

I assume it's because `unified` doesn't ship the node builtins and `vite` also doesn't include them by default.

## Repro

1. Clone this project
2. npm/yarn install
3. npm/yarn dev
4. Access [http://localhost:3000](http://localhost:3000)
