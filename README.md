## 目录
1. [HTML](#HTML)
1. [CSS](#css)
2. [ES5](#es5)
3. [ES6](#es6)
# HTML

## 页面语言LANG
 推荐使用属性值cmn-Hans-CN(简体,中国大陆),但是考虑浏览器和操作系统的兼容性,目前仍然使用zh-CN
 ```
<html lang=”zh-CN”>
 ```

## 元素及标签闭合
HTML元素共有以下5种：
- 空元素：area、base、br、col、command、embed、hr、img、input、keygen、link、meta、param、source、track、wbr
- 原始文本元素：script、style
- RCDATA元素：textarea、title
- 外来元素：来自MathML命名空间和SVG命名空间的元素。
- 常规元素：其他HTML允许的元素都称为常规元素。
元素标签的闭合应遵循以下原则：
- 原始文本元素、RCDATA元素以及常规元素都有一个开始标签来表示开始，一个结束标签来表示结束。
- 某些元素的开始和结束标签是可以省略的，如果规定标签不能被省略，那么就绝对不能省略它。
- 空元素只有一个开始标签，且不能为空元素设置结束标签。
- 外来元素可以有一个开始标签和配对的结束标签，或者只有一个自闭合的开始标签，且后者情况下该元素不能有结束标签。
>  团队约定
为了能让浏览器更好的解析代码以及能让代码具有更好的可读性，有如下约定：
- 所有具有开始标签和结束标签的元素都要写上起止标签，某些允许省略开始标签或和束标签的元素亦都要写上。
- 空元素标签都不加 “/” 字符
> 推荐
```
<div>
    <h1>我是h1标题</h1>
    <p>我是一段文字，我有始有终，浏览器能正确解析</p>
</div>
              
<br>
```
> 不推荐
```
<div>
    <h1>我是h1标题</h1>
    <p>我是一段文字，我有始无终，浏览器亦能正确解析
</div>

<br/>
```
## 书写风格
### HTML代码大小写
HTML标签名、类名、标签属性和大部分属性值统一用小写
> 推荐
```
<div class="demo"></div>
```
> 不推荐
```
<div class="DEMO"></div>
<DIV CLASS="DEMO"></DIV>
```
TML文本、CDATA、JavaScript、meta标签某些属性等内容可大小写混合
```
<!-- 优先使用 IE 最新版本和 Chrome Frame -->
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/>

<!-- HTML文本内容 -->
<h1>I AM WHAT I AM </h1>

<!-- JavaScript 内容 -->
<script type="text/javascript">
               var demoName = 'demoName';
               ...
</script>
             
<!-- CDATA 内容 -->
<script type="text/javascript"><![CDATA[
...
]]></script>
```
## 类型属性
不需要为css丶js指定类型属性,HTML5中默认包含了
> 推荐
```
<link rel="stylesheet" href="" >
<script src=""></script>
```
> 不推荐 
```
<link rel="stylesheet" type="text/css" href="" >
<script type="text/javascript" src="" ></script>
```
## 元素属性
- 元素属性值使用双引号语法
- 元素属性值可以写上的都写上
> 推荐
```
<input type="text">
<input type="radio" name="name" checked="checked" >
```
> 不推荐
```
<input type=text>              
<input type='text'>
<input type="radio" name="name" checked >
```
## 特殊字符引进
文本可以和字符引用混合出现,这种方法可以用来转义在文本中不能合法出现的字符.
在 HTML 中不能使用小于号 “<” 和大于号 “>”特殊字符，浏览器会将它们作为标签解析，若要正确显示，在 HTML 源代码中使用字符实体
> 推荐
```
<a href="#">more&gt;&gt;</a>
```
> 不推荐 
```
<a href="#">more>></a>
```
## 代码缩进
元素嵌套规范，每个块状元素独立一行，内联元素可选
> 推荐
```
<div>
    <h1></h1>
    <p></p>
</div>       
<p><span></span><span></span></p>
```
> 不推荐
```
<div>
    <h1></h1><p></p>
</div>       
<p>
    <span></span>
    <span></span>
</p>
```
## 段落元素与标题元素只能嵌套内联元素
> 推荐
```
<h1><span></span></h1>
<p><span></span><span></span></p>
```
> 不推荐 
```
<h1><div></div></h1>
<p><div></div><div></div></p>
```
## 选择器
- 尽量少用通用选择器 *
- 不使用 ID 选择器
- 不使用无具体语义定义的标签选择器


# CSS
- ## 代码需要格式化后提交
- ## Css代码禁止大写
- ## 尽量少使用选择器
- ## 代码缩进在代码格式化文件
- ## 颜色值中不需要有空格,且取值不要带不必要的0
> 推荐
```
.net {
    color: rgba(255,255,255,.5);
}
```
> 不推荐
```
.net {
    color: rgba(255,255,255,0.5);
}
```
- ## 属性值十六进制数值能用简写尽量简写
- ## 不要为0指定单位
> 推荐:
```
.net {
    margin: 0 10px;
}
```
> 不推荐
```
.net {
    margin: 0px 10px;
}
```
- ## 属性值在引用的时候统一使用单引号

# ES5
## 命名规范
-  ### 文件夹命名语义化
> 推荐
```
home-page
```
> 不推荐 
```
homepage
home_page
```
- ### html,css,js命名
> 推荐
```
<!-- HTML -->
net.html
net-list.html
net-detail.html

<!-- SASS -->
net.scss
net-list.scss
net-detail.scss
```
- className命名
> 推荐
```
<div class="home">
    <p class="home-title"></p>
<div>
```
- 变量命名
 1.关键字不可使用
 2.变量命名小驼峰法
 > 推荐
 ```
 homePage
 ```
 > 不推荐
 ```
 homepage
 HomePage
 ```
 - 函数命名

    1.关键字不可使用

    2.小驼峰法,构造函数大驼峰

 - 常量
 全部大写
 - 类
    - 公共属性和方法同变量名
    - 私有属性和方法 : 前缀为下划线(_)后面跟公共属性和方法一样的命名方式
## 引用
const 和 let 都是块级作用域，var 是函数级作用域
- 对所有引用都使用 const，不要使用 var
> 推荐
```
const a = 1
const b = 2
```
> 不推荐
```
var a = 1
var b = 2
```
- 如果引用是可变动的，则使用 let
> 推荐
```
let count = 1
if (count < 10) {
  count += 1
}
```
> 不推荐
```
var count = 1
if (count < 10) {
  count += 1
}
```
## 对象
1.使用字面量方式创建
> 推荐
```
const item = {};
```
> 不推荐
```
const item=new Object()
```
# ES6
## 箭头函数
1.当你必须使用函数表达式（或传递一个匿名函数）时，使用箭头函数符号
> 推荐
```[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});
```
> 不推荐
```
[1, 2, 3].map(function (x) {
  const y = x + 1;
  return x * y;
});
```
2.如果一个函数适合用一行写出并且只有一个参数，那就把花括号、圆括号和 return 都省略掉。如果不是，那就不要省略。
> 推荐
```
[1, 2, 3].map(x => x * x);
```
> 不推荐
```
[1, 2, 3].reduce((total, n) => {
  return total + n;
}, 0);
```
## 构造器
1.总是使用 class。避免直接操作 prototype 
> 推荐
```
class Queue {
  constructor(contents = []) {
    this._queue = [...contents];
  }
  pop() {
    const value = this._queue[0];
    this._queue.splice(0, 1);
    return value;
  }
}
```
> 不推荐
```
function Queue(contents = []) {
  this._queue = [...contents];
}
Queue.prototype.pop = function() {
  const value = this._queue[0];
  this._queue.splice(0, 1);
  return value;
}
```
2.使用 extends 继承
> 推荐
```
const inherits = require('inherits');
function PeekableQueue(contents) {
  Queue.apply(this, contents);
}


class PeekableQueue extends Queue {
  peek() {
    return this._queue[0];
  }
}
```
> 不推荐
```

inherits(PeekableQueue, Queue);
PeekableQueue.prototype.peek = function() {
  return this._queue[0];
}
```
3.方法可以返回 this 来帮助链式调用
> 推荐
```
class Jedi {
  jump() {
    this.jumping = true;
    return this;
  }

  setHeight(height) {
    this.height = height;
    return this;
  }
}

const luke = new Jedi();

luke.jump()
  .setHeight(20);
```
> 不推荐
```
Jedi.prototype.jump = function() {
  this.jumping = true;
  return true;
};

Jedi.prototype.setHeight = function(height) {
  this.height = height;
};

const luke = new Jedi();
luke.jump(); // => true
luke.setHeight(20); // => undefined
```
4.可以写一个自定义的 toString() 方法，但要确保它能正常运行并且不会引起副作用。
```
class Jedi {
  constructor(options = {}) {
    this.name = options.name || 'no name';
  }

  getName() {
    return this.name;
  }

  toString() {
    return `Jedi - ${this.getName()}`;
  }
}
```
## 模块
1.是使用模组 (import/export) 而不是其他非标准模块系统,你可以编译为你喜欢的模块系统
> 推荐
```
import { es6 } from './NetGuide';
export default es6;
```
> 不推荐
```
const NetGuide = require('./NetGuide');
module.exports = NetGuide.es6;
```
2.不要使用通配符 import
> 推荐
```
import NetGuide from './NetGuide';
```
> 不推荐
```
import * from './NetGuide';
```
3.不要从 import 中直接 export
> 推荐
```
import { es6 } from './NetGuide';
export default es6;
```
> 不推荐
```
export { es6 as default } from './NetGuide';
```
## 属性
1.使用 . 来访问对象的属性。
> 推荐
```
const luke = {
  jedi: true,
  age: 28,
};
const isJedi = luke.jedi;
```
> 不推荐
```
const isJedi = luke['jedi'];
```
2.当通过变量访问属性时使用中括号 []
```
const luke = {
  jedi: true,
  age: 28,
};

function getProp(prop) {
  return luke[prop];
}

const isJedi = getProp('jedi');
```
## 比较运算符和等号
1.优先使用 === 和 !== 而不是 == 和 !=
2.条件表达式例如 if 语句通过抽象方法 ToBoolean 强制计算它们的表达式并且总是遵守下面的规则：
- 对象 被计算为 true
- Undefined 被计算为 false
- Null 被计算为 false
- 布尔值 被计算为 布尔的值
- 数字 如果是 +0、-0、或 NaN 被计算为 false, 否则为 true
- 字符串 如果是空字符串 '' 被计算为 false，否则为 true
> 推荐
```
if (name) {
  // ...stuff...
}
if (collection.length) {
  // ...stuff...
}
```
> 不推荐
```
if (name !== '') {
  // ...stuff...
}
if (collection.length > 0) {
  // ...stuff...
}
```

