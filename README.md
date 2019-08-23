# TypeScript Project Generator

An opinionated project generator for TypeScript projects.

## Usage

To run it just once:

```sh
$ npx <TODO>
```

If you find yourself using the generator for a lot of new projects, we recommend [Volta], which has a [great story][globals] around “global” installs:

[Volta]: https://volta.sh
[globals]: https://blog.volta.sh/2019/06/18/global-installs-done-right/

```sh
$ volta install <TODO>
$ <TODO>
```

## The opinions

- Use Babel for compilation.
- Use the equivalent of `strict: true`
- Generate ES Modules

### Use Babel for compilation

TypeScript and Babel’s compilation output differs in subtle but important ways for some proposed JavaScript features, especially decorators. In order to guarantee correct interop between libraries generated with this tool and the JavaScript ecosystem, TypeScript is used only for type-checking, *not* for compilation.

### Use the equivalent of `strict: true`

TypeScript is most useful with all of its strictness settings turned on. However, as a matter of *stability*, actually using `strict: true` can cause code to stop compiling between minor releases. By setting these configuration options manually, the generator can improve backwards-compatible stability between upgrades, with users able to opt into new levels of strictness at will rather than it being forced by a TypeScript version release (which may be desired for other reasons).

### Generate ES Modules

[ECMAScript Modules][modules] are the language standard module format, are supported in all modern/evergreen browsers, and are [on track][node] to be fully supported by Node.js. Where interop with other module systems is necessary, all modern bundlers support transforming ES Modules into the target format.

[modules]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules
[node]: https://nodejs.org/api/esm.html#esm_ecmascript_modules