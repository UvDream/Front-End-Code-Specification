# Vue前端规范

## - 组件名为多个单词

这样避免与html冲突

## - props尽量详细,最好指定默认类型

## - v-for设置键

## - v-for 和v-if不要放在一起使用

## - 组件样式设置作用域 scoped

## - 模板下的简单的表达式

> 推荐

```
!-- 在模板中 -->
{{ normalizedFullName }}
// 复杂表达式已经移入一个计算属性
computed: {
  normalizedFullName: function () {
    return this.fullName.split(' ').map(function (word) {
      return word[0].toUpperCase() + word.slice(1)
    }).join(' ')
  }
}
```

> 不推荐

```
{{
  fullName.split(' ').map(function (word) {
    return word[0].toUpperCase() + word.slice(1)
  }).join(' ')
}}
```

## - 私有属性

在插件、混入等扩展中始终为自定义的私有属性使用 $_ 前缀。并附带一个命名空间以回避和其它作者的冲突 (比如 $_yourPluginName_)。

> 推荐

```
var myGreatMixin = {
  // ...
  methods: {
    $_myGreatMixin_update: function () {
      // ...
    }
  }
}
```

> 不推荐

```
var myGreatMixin = {
  // ...
  methods: {
    update: function () {
      // ...
    }
  }
}
var myGreatMixin = {
  // ...
  methods: {
    _update: function () {
      // ...
    }
  }
}
var myGreatMixin = {
  // ...
  methods: {
    $update: function () {
      // ...
    }
  }
}
var myGreatMixin = {
  // ...
  methods: {
    $_update: function () {
      // ...
    }
  }
}
```

# 特别说明

## 1.注释

建议使用VscCode插件koroFileHeader
自动生成文件注释头

```
/*
 * @Author: wangzhongjie
 * @LastEditors: wangzhongjie
 * @Description: 复用路由
 * @Date: 2019-04-11 11:06:25
 * @LastEditTime: 2019-04-11 14:06:44
 */
```

## 2.严禁在框架内使用jQuery!!!!!

## 3.前端代码编辑器建议使用VsCode或者能使用Eslint编辑器,推荐Eslint结合Prettier