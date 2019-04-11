# ES5规范
## 注释规范
- 单行注释
```
<!--注释-->

```
- 多行注释
```
/*
*
*/
```
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



