两个操作都使a和b的值变成30，但是，这样看起来似乎前置操作符和后置操作符的结果是一样的，再来看这样一个例子：

```JavaScript
// 前置操作符
let num1 = 2;
let num2 = 20;
let num3 = --num1 + num2;
let num4 = num1 + num2;
console.log(num3); // 21
console.log(num4); // 21

// 后置操作符
let num1 = 2;
let num2 = 20;
let num3 = num1-- + num2;
let num4 = num1 + num2;
console.log(num3); // 22
console.log(num4); // 21
```

在前置操作符中，num3在计算时num1的取值是1，在后置操作符中，num3在计算时num1的取值是2，这说明：

- 在与其他计算混合时，前置操作符会取计算后的值参与运算，后置操作符会取原值参与运算，最后在将使用递增/递减操作符的变量重新计算赋值。

递增/递减操作符不仅可以计算数字类型的数据，对于其他数据类型也可以计算，具体规则如下：

- 字符串

```JavaScript
let s1 = "2";
s1++; // 值变成3，类型为数字

let s2 = "a";
s2++; //  值变成NaN，类型为数字
```

- 布尔值

```JavaScript
let b = false;
b++; // false会转变成0，再参与运算，最终结果为1

let c = true;
c++; // true会转变成1，再参与运算，最终结果为2
```

- 浮点值

```JavaScript
let f = 1.1;
f--; // 值变成 0.10000000000000009（因为浮点数不精确） 
```

- 对象

```JavaScript
let o = {
  valueOf() {
    return -1;
  }
};
o--; // 值变成-2 
// 应用给对象时，操作符通常会调用 valueOf()和/或 toString()方法来取得可以计算的值。 
```