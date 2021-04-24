# WASM Experiment

This is just to see what this [WebAssembly](https://webassembly.org) malarky is all about.

## Info for running

This is all coming from [this guide](https://github.com/golang/go/wiki/WebAssembly#getting-started) as I am a bit of a noob to wasm at this point.

Command to build wasm file:

```bash
GOOS=js GOARCH=wasm go build -o out/main.wasm cmd/main.go
```

Command to get wasm_exec.js:

```bash
cp "$(go env GOROOT)/misc/wasm/wasm_exec.js" scripts/
```

Command to start serving this to test out:

```bash
goexec 'http.ListenAndServe(`:8080`, http.FileServer(http.Dir(`.`)))'
```

Then open a browser and check the console logs:

```bash
open http://localhost:8080/public/
```

NOTE: For whatever reason, wasm cannot be executed on Safari [yet](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WebAssembly/instantiateStreaming#browser_compatibility), so use Chrome or another modern browser.

TODO:

- [X] Get a basic Go WASM app working
- [ ] Transition most of the project to use [Please](https://please.build)
- [ ] Perhaps make a go -> wasm plz build def
- [ ] Reflect on why you are wasting your time doing this rather than doing something that actually makes money
