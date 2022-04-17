Learn WASM
---

Taking some notes while typing it out.

- https://github.com/WebAssembly/wabt
- https://github.com/wasm3/wasm3
- https://wasmtime.dev
- https://webassembly.github.io/spec/core/appendix/index-instructions.html
- https://webassembly.github.io/wabt/demo/wat2wasm/

Install via brew

```
brew install wabt
brew install wasm3
brew install wasmtime
```

> Note: Can't install via command line on Mac M1 for wasmtime : reference : https://github.com/bytecodealliance/wasmtime/pull/3983


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