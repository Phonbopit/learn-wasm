Learn WASM
---

Taking some notes while typing it out. (No structure, no format)

Random learning with:

- [Book] - WebAssembly - The Definitive Guide
- https://wasmbyexample.dev
- https://webassembly.org/getting-started/developers-guide/
- https://developer.mozilla.org/en-US/docs/WebAssembly
- https://github.com/sunfishcode/wasm-reference-manual/blob/master/WebAssembly.md

## Things I want to learn

- https://github.com/WebAssembly/wabt
- https://github.com/wasm3/wasm3
- https://wasmtime.dev
- https://webassembly.github.io/spec/core/appendix/index-instructions.html
- https://webassembly.github.io/wabt/demo/wat2wasm/
- https://github.com/WebAssembly/binaryen
- https://github.com/wasmerio/wasmer
- https://github.com/yewstack/yew
- https://github.com/rustwasm/wasm-pack
- https://rustwasm.github.io/docs/book/
- https://github.com/mbasso/awesome-wasm

#### VS Code

- - WebAssembly Toolkit for VSCode - https://marketplace.visualstudio.com/items?itemName=dtsvet.vscode-wasm

#### Install via brew

```
brew install wabt
brew install wasm3
brew install wasmtime
```

> Note: I can't install via command line on Mac M1 for wasmtime : reference : https://github.com/bytecodealliance/wasmtime/pull/3983

- WAT is WebAssembly Text Format
- wabt - pronounced "wabbit"

```
error: unexpected token get_local, expected )
```

- Use `local.get` instead of `get_local` - reference : https://github.com/WebAssembly/wabt/issues/1820
- internal named start with `$`, the exported version does not.
- data types have only i32, i64, f32 and f64

```
wat2wasm add.wat
```

Running wasm in a Repl

```
wasm3 --repl simple.wasm

wasm3> addTwo 2 3
Result: 5
```

- Web Assembly on browser : https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WebAssembly/Instance

```
python3 -m http.server
```

#### Module Structure

Empty WASM module.

```wat
(module)
```

```
wat2wasm empty.wat

-rw-r--r--  1 chai  staff  8 Apr 17 19:04 empty.wasm
```

```
wasm-objdump -x empty.wasm
```

#### recommneded way to instantiate modules

```js
(async () => {
  const fetchPromise = fetch(url);
  const { instance } = await WebAssembly.instantiateStreaming(fetchPromise);

  console.log('instance', instance);
})();
```

- Promise instead of `ArrayBuffer` -> `bytes`
- Proposal ES Module - https://github.com/WebAssembly/esm-integration