This code is follow along of the tutorial : https://evilmartians.com/chronicles/hands-on-webassembly-try-the-basics

I used emscripten here but I will also use the Clang LLVM compiler in further days. 

Once the code is saved in dragon-curve.c file, I have ran an `emcc` command to compile the file into wasm and give an `js` file output. 

```
emcc dragon-curve.c -Os -o dragon-curve.js \
-s EXPORTED_FUNCTIONS='["_dragonCurve", "_malloc", "_free"]' \
-s EXPORTED_RUNTIME_METHODS='["ccall"]' \
-s MODULARIZE=1
```

Here’s what it does: ( I only know details of some flags, rest I copied)

- `-Os` tells emscripten to optimize for size: both for Wasm and JS
- Note that we only need to specify the .js file name as the output, .wasm is generated automatically.
- We can also choose which function we want to export from the resulting Wasm module, note that it requires an underscore before the name, hence `-s EXPORTED_FUNCTIONS='["_dragonCurve", "_malloc", "_free"]'`. The last two functions will help us work with memory.
- As our source code is C, we also have to export the `ccall` function that emscripten generates for us.
- `MODULARIZE=1` allows us to use a global Module function that returns a Promise with an instance of our wasm module.

Next create a html file that will use the `.js` file created along with some script for memory and display details.

![Fw6CZkGWAAgm7ku](https://github.com/karnatisrinivas/lets-wasm/assets/52213014/b92b4592-eb7e-40d8-8b1f-beadabd7f25b)
