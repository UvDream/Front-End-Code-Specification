# ES6规范
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