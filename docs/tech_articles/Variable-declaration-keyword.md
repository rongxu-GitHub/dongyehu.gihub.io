### 变量声明关键字的区别

在JavaScript中，变量是松散类型的，可以保存任意类型的数据，不必像Java中需要声明变量的类型。

声明变量有3个关键字：`var`、`const`和`let`。

var可以在任何ECMAScript版本中使用，而const和let只能在ECMAScript6及以后的版本中使用。

var声明为函数作用域，let和const为块作用域，let和const的用法类似，同一作用域内不允许声明重复变量，变量赋值后不可更改。

实际使用中，const优先，let次之，var少用。