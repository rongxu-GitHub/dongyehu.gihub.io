### 函数的方法-apply()和call()

#### apply()

apply()接收两个参数：

- this

- 参数数组或arguments对象

下面两个例子的最终结果都是一样的：

```JavaScript
function sum(num1, num2) {
return num1 + num2;
}

function callSum1(num1, num2) {
return sum.apply(this, arguments); // 传入 arguments 对象
}

function callSum2(num1, num2) {
return sum.apply(this, [num1, num2]); // 传入数组
}

console.log(callSum1(10, 10)); // 20
console.log(callSum2(10, 10)); // 20

```

#### call()

call()方法和apply()方法的作用是一样的，只是传参的方式不一样。

通过 call()向函数传参时，必须将参数一个一个地列出来，不能传递数组和arguments。

```JavaScript
function sum(num1, num2) {
return num1 + num2;
}

function callSum(num1, num2) {
return sum.call(this, num1, num2);
}
```

如果想直接传 arguments对象或者一个数组，那就用 apply()；否则，就用 call()。
