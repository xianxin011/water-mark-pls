

[![](https://img.shields.io/badge/Powered%20by-xianxin%20-brightgreen.svg)](https://github.com/xianxin011/water-mark-pls)
[![GitHub license][license-image]][license-url]
[![GitHub stars][stars-image]][stars-url]
[![GitHub forks][forks-image]][forks-url]
[![GitHub issues][issues-image]][issues-image]
[![npm download][download-image]][download-url]

[license-image]: https://img.shields.io/github/license/xianxin011/watermark-dom.svg
[license-url]: https://github.com/xianxin011/water-mark-pls/blob/master/LICENSE
[stars-image]: https://img.shields.io/github/stars/xianxin011/watermark-dom.svg
[stars-url]: https://github.com/xianxin011/water-mark-pls/stargazers
[forks-image]: https://img.shields.io/github/forks/xianxin011/watermark-dom.svg
[forks-url]: https://github.com/xianxin011/water-mark-pls/network
[issues-image]: https://img.shields.io/github/issues/xianxin011/watermark-dom.svg
[issues-url]: https://github.com/xianxin011/water-mark-pls/issues
[download-image]: https://img.shields.io/npm/dm/watermark-dom.svg
[download-url]: https://npmjs.org/package/watermark-dom
[hits-image]: http://hits.dwyl.io/xianxin011/https://githubcom/xianxin011/watermark-dom.svg

`watermark.js`是基于DOM对象实现的BS系统的水印，确保系统保密性，安全性，降低数据泄密风险，简单轻量，支持多属性配置，动态计算水印，水印防被删（监听水印组件元素删除并重新添加，监听改变水印的属性并重新添加）。

特性：

+ 多属性配置，简单易上手
+ 动态计算水印
+ **水印防被删(监听水印组件元素删除并重新添加，监听改变水印的属性并重新添加)**
+ 支持2种导入使用：本地引用，npm引用
+ 水印测试工具：testTool工具
+ 内置3种全局API方法：init()，load(), remove()。
+ 原理：pointer-events事件穿透属性，Shadow DOM(影子DOM)，opacity等

注意：基于本项目源码从事科研、论文、系统开发，"最好"在文中或系统中表明来自于本项目的内容和创意，否则所有贡献者可能会鄙视你和你的项目。 使用本项目源码请尊重程序员职业和劳动

## 1、版本及功能

+ 版本v 1.0.0
  - 1、支持文本水印；
  - 2、支持本地js，支持npm包；
  - 2、支持浏览器：Chrome，Firefox，Safari；
  - 3、支持api
  - 4、监听前端页面手动删除水印挂载的父元素，或删除影子DOM里的单个水印，当删除时会自动添加新水印

## 2、水印插件-使用

### 2.1 本地引入封装的js文件

只是简单的加一个很浅的水印，实现起来很容易。

`watermark.js`是必须要引进的组件

第一步：获取组件方式：`git clone https://github.com/xianxin011/water-mark-pls.git`

第二步：clone后，在需要加水印的相关页面引入水印文件"watermark.js":

```
<script type="text/javascript" src="./watermark.js"></script>
```

第三步：在确保页面DOM加载完毕之后，调用watermark的load方法(手动加载):

```
   <script>watermark.load({ watermark_txt: "测试水印，1021002301，测试水印，100101010111101" })</script>
```

注意：我们提供了init方法，用来初始化水印，添加load和resize事件

```
   <script>watermark.init({ watermark_txt: "测试水印，1021002301，测试水印，100101010111101" })</script>
```


![image](https://github.com/xianxin011/water-mark-pls/blob/master/examples/image/simple.png)

### 2.2 npm包引入

第一步：npm获取水印组件包：

```
npm install water-mark-pls
```

第二步：引入水印模块：

```
import watermark from 'water-mark-pls'
或者
var watermarkDom = require("water-mark-pls")
```

第三步：在确保页面DOM加载完毕之后，调用watermark的load方法(手动加载):

```
   <script>watermark.load({ watermark_txt: "测试水印，1021002301，测试水印，100101010111101" })</script>
```

注意：(1)我们提供了init方法，用来初始化水印，添加load和resize事件

```
   <script>watermark.init({ watermark_txt: "测试水印，1021002301，测试水印，100101010111101" })</script>
```

注意：(2)我们提供了remove方法，用来移除水印

```
   <script>watermark.remove({ watermark_txt: "测试水印，1021002301，测试水印，100101010111101" })</script>
```

## 3、水印demo（测试工具）

查看地址：https://github.com/xianxin011/water-mark-pls/blob/master/examples/simple/index.html


## 4、内置方法

### 4.1 watermark.init(setting);

初始化水印，添加load和resize事件

例子

```js
watermark.init({ watermark_txt: "测试水印，1021002301，测试水印，100101010111101" });
```

### 4.2 watermark.load(setting);

手动加载水印

例子

```js
watermark.load({ watermark_txt: "测试水印，1021002301，测试水印，100101010111101" });
```

### 4.3 watermark.remove();

手动移除水印

例子

```js
watermark.remove();
```

## 5、支持各种属性配置使用

```
watermark_id: 'wm_div_id',          //水印总体的id
watermark_prefix: 'mask_div_id',    //小水印的id前缀
watermark_txt:"测试水印",             //水印的内容
watermark_x:20,                     //水印起始位置x轴坐标
watermark_y:20,                     //水印起始位置Y轴坐标
watermark_rows:0,                   //水印行数
watermark_cols:0,                   //水印列数
watermark_x_space:100,              //水印x轴间隔
watermark_y_space:50,               //水印y轴间隔
watermark_font:'微软雅黑',           //水印字体
watermark_color:'black',            //水印字体颜色
watermark_fontsize:'18px',          //水印字体大小
watermark_alpha:0.15,               //水印透明度，要求设置在大于等于0.005
watermark_width:100,                //水印宽度
watermark_height:100,               //水印长度
watermark_angle:15,                 //水印倾斜度数
watermark_parent_width:0,      //水印的总体宽度（默认值：body的scrollWidth和clientWidth的较大值）
watermark_parent_height:0,     //水印的总体高度（默认值：body的scrollHeight和clientHeight的较大值）
watermark_parent_node:null     //水印插件挂载的父元素element,不输入则默认挂在body上
watermark_color_size: 10,      //水印的随机颜色数量，如果使用这个值，watermark_color将会失效
watermark_angle_random: true, //水印的旋转角度随机
```

上面的属性都支持配置的，怎么使用呢？

基本山需要自己配置的属性：`watermark_txt`,`watermark_color`,`watermark_fontsize`,`watermark_alpha`,`watermark_angle`，`watermark_width`,`watermark_height`这7个属性一般是经常用到的，其他属性一般用的偏少。需要用到的就设置一下，不需要用到的就可以不设置，插件内部会有默认值的。

比如load方法的属性配置

```
 watermark.load({
    watermark_txt: '1050226 xianxin_',  //水印的内容
    watermark_color:'#5579ee',            //水印字体颜色
    watermark_fontsize:'24px',          //水印字体大小
    watermark_alpha:0.5,               //水印透明度，要求设置在大于等于0.005
    watermark_angle:135,                 //水印倾斜度数
    watermark_width:200,                //水印宽度
    watermark_height:200,               //水印长度
});
```

## 6、支持浏览器

Chrome,FireFox,Safari,IE9及以上浏览器