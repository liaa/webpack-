这个 repo 介绍一些 Webpack 常用的应用场景.

1. [require 非标准模块格式的代码(不遵循CommonJS,也不遵循AMD)](#require-非标准模块格式的代码(不遵循CommonJS,也不遵循AMD))

### require 非标准模块格式的代码(不遵循CommonJS,也不遵循AMD)

假设我们有一个 ./rocket.js 文件,内容如下:

```
    var rocket = {
        fly: function() {
            console.log('hu~~~, hu~~~');
        }
    }
```

`rocket.js` 属于非标准格式的模块, 我们需要使用 [exports-loader](https://github.com/webpack/exports-loader) 来引用.

            npm install exports-loader; // 安装 exports-loader
            
在需要使用的地方只需要这样写:

```
    var myRocket = require('exports?rocket!./rocket.js');
    myRocket.fly();   
    
    // will produce "hu~~~, hu~~~"
```
    
exports-loader 更多的使用方法参考 [shimming-modules](https://webpack.github.io/docs/shimming-modules.html) 的EXPORTING部分.









## 知识点
1. imports-loader 使用 https://github.com/webpack/imports-loader
2. exports-loader 使用 https://github.com/webpack/exports-loader
3. [plugin ProvidePlugin 来实现一个全局默认可用的 module](globalPlugin)
4. script-loader 使用 
5. expose-loader 使用 https://github.com/webpack/expose-loader

### <a name="globalPlugin"></a> ProvidePlugin 全局可用的 module

```
new webpack.ProvidePlugin({
    $: "jquery",
    jQuery: "jquery",
    "window.jQuery": "jquery"
})
```





