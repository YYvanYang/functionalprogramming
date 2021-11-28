---
layout: cover
highlighter: shiki
info: |
  ## 函数式编程

  JavaScript函数式编程

  Yvan Yang
---

# 函数式编程

JavaScript函数式编程

<div class="uppercase text-sm tracking-widest">
Yvan Yang
</div>

---
name: 函数式编程
layout: center
---

<div class="grid grid-cols-[3fr,2fr] gap-4">
  <div class="text-center pb-4">
    <img class="h-50 inline-block" src="/ramda.png">
    <div class="opacity-50 mb-2 text-sm">
      主要内容
    </div>
  </div>
  <div class="border-l border-gray-400 border-opacity-25 !all:leading-12 !all:list-none my-auto">

  - 什么是函数式编程？
  - 为什么推荐函数式编程？
  - 高阶函数(higher-order function)
  - 闭包之函数柯里化(Currying)
  - 不可变(Immutability)
  - 纯之门路

  </div>
</div>

---
layout: image-left
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# 什么是函数式编程？

### 特性

<div v-click>

- 纯粹的(pure)
- 无状态(stateless)
- 高阶(higher-order)
- 副作用(side effect)
- 不可变(immutable)
- 柯里化(currying)
- 组合(compose)

</div>

---
layout: center
---

# 编程范式(Programming paradigm)[^1]

<br />
<br />

<div class="grid grid-cols-2 gap-x-4 gap-y-4">

<div>

### 命令式||过程式(Imperative)

- 跟随我的指令，先执行这个，再执行那个。。。

</div>

<div>

### 说明式||声明式(Declarative)

- 基于模板的 html，css

</div>

<div>

### 面向对象编程(Object-Oriented)

- 封装、继承、多态
- 有自己的状态

</div>

<div>

### 函数式编程（functional programming）

- 将计算描述为一种表达式求值

</div>

</div>

[^1]: [再谈编程范式—程序语言背后的思想](https://imweb.io/topic/5cde5770e363b77a0edeb874)

---
layout: center
---

# 函数式编程之根---纯函数(pure functions)

- 如果函数的调用参数相同，则永远返回相同的结果。它不依赖于程序执行期间函数外部任何状态或数据的变化，必须只依赖于其输入参数。
- 该函数不会产生任何可观察的副作用，例如网络请求，输入和输出设备或数据突变（mutation）。

<v-click>

> 2句话总结：相同输入相同输出，没有改变外部的环境！

</v-click>

---

# 保持组件纯度

<iframe src="https://codesandbox.io/embed/sandpack-project-forked-8qtv3?fontsize=14&hidenavigation=1&theme=dark"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="sandpack-project (forked)"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>

---
layout: center
---

  <img border="rounded" src="/i_puritea-recipe.png">

  <div class="text-center text-green-500">
  <span>五香茶</span>
  </div>

---

# 副作用

<iframe src="https://codesandbox.io/embed/peaceful-rosalind-tles0?fontsize=14&hidenavigation=1&theme=dark"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="peaceful-rosalind-tles0"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>

[-] [Detecting unexpected side effects](https://reactjs.org/docs/strict-mode.html#detecting-unexpected-side-effects)
[-] [In StrictMode, the useState() initializer function is called twice](https://github.com/facebook/react/issues/20090#issuecomment-715927125)

# 为什么推荐函数式编程？

### 价值所在
<v-click>

- 更加可预测性
- 更易被测试/调试
- 更加可靠（幂等操作）

</v-click>


---
layout: image-right
image: https://source.unsplash.com/collection/94734561/1920x1080
---

# 纯与不纯


###### 不纯 ? or 纯 ?

```js
function getDate() {
  return new Date().toDateString();
}
```

<br />


###### 不纯 ? or 纯 ?

```js
function getDate (year, month, day) {
  return new Date(year, month, day).toDateString();
}
```

---
layout: image-right
image: https://source.unsplash.com/collection/94734121/1920x1080
---

# 高阶函数

- filter, map, reduce

---

# 闭包之函数柯里化

```js
function curry(func) {

  return function curried(...args) {
    if (args.length >= func.length) {
      return func.apply(this, args);
    } else {
      return function(...args2) {
        return curried.apply(this, args.concat(args2));
      }
    }
  };

}
```
---

# 例子

```js
function sum(a, b, c) {
  return a + b + c;
}

let curriedSum = curry(sum);

alert( curriedSum(1, 2, 3) ); // 6，仍然可以被正常调用
alert( curriedSum(1)(2,3) ); // 6，对第一个参数的柯里化
alert( curriedSum(1)(2)(3) ); // 6，全柯里化
```

---

# 不可变(Immutability)

- 写拷贝(Copy-on-Write)

todo

---

# 纯之门路

- todo

