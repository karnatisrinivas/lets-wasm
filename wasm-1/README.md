## Hello Luffy 

```
#include <stdio.h>

int main() {
    printf("Hello Luffy\n");
    return 0;
}
```

The above program is in C and will return "Hello Luffy" when executed. <- this thing you all know. 

### lets try wasm 

Let's run the above program as wasm compiled binary. Inorder to do that, we need to install some tools. 

We will use <b>emscripten</b> as the compiler tool for WASM. You can install emscripten using the following commands.

```
git clone https://github.com/emscripten-core/emsdk.git
cd emsdk
./emsdk install latest
./emsdk activate latest
source ./emsdk_env.sh
```

Once you have installed and configured the emscripten, you can compile our `main.c`. 

```
emcc main.c -o index.html
```

The above command will compile the `c` file into `main.wasm` file and it also gives an `index.html` page that you can use to run the compiled code on the browser. (compiled code in javascript). You can also get output file in .js file. 

```
emcc main.c -o main.js

// you can run compiled code using 

node main.js
```

### I also tried "wasmedge" as runtime. 

Installing wasmedge is very simple. All you have to do is to run these commands in linux/macos machine:

```
curl -sSf https://raw.githubusercontent.com/WasmEdge/WasmEdge/master/utils/install.sh | bash
source $HOME/.wasmedge/env
```


Once the wasmedge is installed, you can run the compiled binary using wasmedge. 

```
emcc main.c -o compiled.wasm 

// above command will give a wasm compiled binary, you can execute using the following

wasmedge compiled.wasm
```


### Tutorials 

https://www.youtube.com/watch?v=7553XZ0T6pM 

https://wasmedge.org/docs/develop/c/hello_world/
