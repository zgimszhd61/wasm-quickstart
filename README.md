WebAssembly (Wasm) 是一种为高性能应用程序设计的低级字节码格式，它允许在网页浏览器中运行接近原生性能的代码。以下是一个简单的Wasm快速入门教程，包括如何编写、编译和在网页中运行一个简单的WebAssembly模块。

## 步骤1: 编写C代码

首先，我们需要编写一个简单的C函数。这个函数将计算一个整数的平方。创建一个名为`square.c`的文件，并添加以下代码：

```c
int square(int num) {
    return num * num;
}
```

## 步骤2: 编译C代码为Wasm

接下来，我们需要将C代码编译为WebAssembly。这需要使用Emscripten编译器。如果你还没有安装Emscripten，请参考[官方安装指南](https://emscripten.org/docs/getting_started/downloads.html)进行安装。

安装完成后，打开终端或命令提示符，导航到包含`square.c`文件的目录，并运行以下命令来编译它：

```bash
emcc square.c -s WASM=1 -o square.js
```

这将生成两个文件：`square.js`（加载和运行Wasm模块的JavaScript "胶水"代码）和`square.wasm`（编译后的WebAssembly模块）。

## 步骤3: 在网页中使用Wasm模块

最后，我们需要在网页中加载和运行这个Wasm模块。创建一个名为`index.html`的HTML文件，并添加以下代码：

```html
<!DOCTYPE html>
<html>
<head>
    <title>Wasm Quickstart</title>
</head>
<body>
    <script src="square.js"></script>
    <script>
        // 加载Wasm模块
        Module.onRuntimeInitialized = async _ => {
            // 调用Wasm模块中的square函数
            const result = Module._square(9);
            console.log('9的平方是: ' + result);
        };
    </script>
</body>
</html>
```

这段代码首先加载`square.js`，该文件包含了必要的胶水代码来加载和初始化Wasm模块。然后，它等待Wasm模块初始化完成，并调用`Module._square`函数来计算9的平方，并将结果打印到控制台。

## 结论

通过以上步骤，你已经成功编写、编译并在网页中运行了一个简单的WebAssembly模块。这只是WebAssembly的冰山一角，但希望它能作为你深入学习和探索WebAssembly世界的起点[1][2][3][7][8]。

Citations:
[1] https://www.freecodecamp.org/news/get-started-with-webassembly-using-only-14-lines-of-javascript-b37b6aaca1e4/
[2] https://wasmbyexample.dev/examples/hello-world/hello-world.assemblyscript.en-us
[3] https://tutorialzine.com/2017/06/getting-started-with-web-assembly
[4] https://www.youtube.com/watch?v=ojYEfRye6aE
[5] https://www.youtube.com/watch?v=_8T9T6MQ1fU
[6] https://www.youtube.com/watch?v=dqhJU772ckM
[7] https://thenewstack.io/webassembly-and-go-a-guide-to-getting-started-part-1/
[8] https://webassembly.org/getting-started/developers-guide/
