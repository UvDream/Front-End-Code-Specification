# HTML规范

## DOCTYPE 声明
一个doctype必须包含以下部分,并严格按照顺序出现
1. 一个ASCII字符串 “<!DOCTYPE” ，大小写不敏感
2. 一个或多个空白字符
3. 一个ASCII字符串”html”，大小写不敏感
4. 一个可选的历史遗留的DOCTYPE字符串 （DOCTYPE legacy string），或者一个可选的已过时但被允许的DOCTYPE字符串 （obsolete permitted DOCTYPE string） 字符串
5. 一个或多个空白字符
6. 一个编码为 U+003E 的字符 “>”
> 团队约定
  HTML文件必须加上DOCTYPE声明,并统一使用HTML5的文档声明:
  ```
    <!DOCTYPE html>
  ```

## 页面语言LANG
 推荐使用属性值cmn-Hans-CN(简体,中国大陆),但是考虑浏览器和操作系统的兼容性,目前仍然使用zh-CN
 ```
<html lang=”zh-CN”>
 ```
### CHARSET
- Unicode标准覆盖了几乎所有字符丶标点符号和符号
- Unicode使用文本的处理丶存储和运输,独立于平台和语言
- HTML-5中默认的字符编码UTF-8

>  团队约定
一般情况下统一使用”UTF-8”编码
```
<meta charset=”UTF-8”>
 ```
由于历史原因,有些业务可能会使用”GBK”编码
```
<meta charset=”GBK”>
```
请尽量统一写成标准的”UTF-8”,不要写成”utf-8”或者”utf8”或者”UTF8”. 根据 IETF对UTF-8的定义，其编码标准的写法是 “UTF-8”；而 UTF8 或 utf8 的写法只是出现在某些编程系统中，如 .NET framework 的类 System.Text.Encoding 中的一个属性名就叫 UTF8。
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

