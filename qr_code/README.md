# Frontend mentor - qr_code

This is a solution to the [QR code component challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/qr-code-component-iux_sIO_H). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

### What I Learned

#### 动态 imgUrl 概念学习

- assets 文件和 static 文件的区别

assets 文件会在 npm run dev 或 npm run build 的情况下被 webpack 处理为 **模块依赖 ，仅支持相对路径的方式**

static 文件不会被 webpack 处理，会被直接复制到 dist/static 文件下，须采用**绝对路径**的形式

- 为什么要加上 require [require 动态引入图片](https://blog.csdn.net/longxiaobao123/article/details/130440099)

因为动态添加 src 被当做静态资源处理了，而被编译过后的静态路径无法正确的引入资源，所以要加上 require

-- 静态资源
-- 动态资源

- require 是什么？如何作用

是一个 node 方法，用于引入模块、JSON 或本地文件

vue 通过 webpack 打包，webpack 打包规则针对的是每一个模块，即 webpack 仅会对模块打包。

- 调用 require 后

  - 1.如果这张图片小于项目中设置的资源限制大小，则会返回图片的 base64 插入到 require 方法的调用处
  - 2.如果这张图片大于项目中设置的资源限制大小，则会将这个图片编译成一个新的图片资源。require 方法返回新的图片资源路径及文件名

> require 拿到的文件地址是 **资源文件编译后的地址**（dist 下的文件/base64 文件）因此可找对应文件，以成功引入资源

##### Question

```
<img :src="./img/test.png" :alt="">   // 不生效

```

##### Solution

```
*****Method 1*****vue2写法***

<img :src="require('@/assets/img/components/dialog-title.png')" alt="" />

*****Method 2*****vue2写法***

<img :src="imgUrl" />

data(){
    return {
        imgUrl: require('@/assets/img/home/day.png'),
    }
}

```

#### 怎么配置 @===》src

使用 path 模块为 src 目录配置别名

```
//vite.config.js

import {defineConfig} from 'vite'
import path from 'path'
import vue from 'vue'
export default defineConfig({
    plugins:[vue()],
    resolve:{
        alias:{
            "@": path.resolve(__dirname,"./src")
        }
    }
})

// tsconfig.json

{
    "compilerOptions":{
        "baseUrl":"./",
        "paths":{
            "@/*":["./src/*"],
            "style/*":["./src/styles/*"]
        }
    }
}

```

### css 布局

- flex 布局
- flex：1 ？？

### node-saa 了解

- 采用 lang="scss"之后报错 ‘can‘t find module sass’
- npm i node-sass
  在安装 node-sass 之前，我先介绍一下什么是 node-sass。node-sass 是一个项目依赖，在一个项目中在使用 sass 语法的时候，必须通过 sass-loader 来解析 sass，从而使 sass 语法变成浏览器能够识别的 CSS 语法，而 node-sass 模块就是对 sass-loader 的支持模块，所以不安装 node-sass，sass-loader 就不能正常工作

-sass scss 的区别

## Author

- Website - [Xin jie Feng](https://github.com/calmfff/frontendment_repo)

## Acknowledgments

- Website - [Xiang Li](https://github.com/LixiangHello)