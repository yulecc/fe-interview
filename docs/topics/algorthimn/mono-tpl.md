# 实现一个极简的模板引擎

## 题目描述

实现函数 render, 是的返回符合预期。

```js
render("我是{{name}}，年龄{{age}}", {
  name: "lucifer",
  age: 17
});

// 结果： 我是姓名，年龄18
```
## 关键点

正则表示默认是`贪婪匹配`，如果实现懒惰匹配，在量词元字符后面添加一个`？`即可。

如果使用贪婪匹配，我们会匹配到最后一个}}，而不是第一个结束的}}。
## 代码

```js
function render(tpl, data) {
  return tpl.replace(/\{\{(.+?)\}\}/g, function($1, $2) {
    // $1 分组为 类似 {{name}}
    // $2 分组为 类似 name
    // 加上面的小括号就是为了方便拿到key而已
    return data[$2];
  });
}
```
