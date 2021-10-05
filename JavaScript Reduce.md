# JavaScript中Reduce() 的6个用例

英文 | https://betterprogramming.pub/6-use-cases-for-reduce-in-javascript-49683842ebed

reduce 方法在数组的每个元素上执行用户提供的回调函数，即“reducer”。它传入对前一个元素进行计算的返回值。结果是单个值。它是在数组的所有元素上运行 reducer 的结果。

**它是如何工作的？**

reducer 函数逐个遍历数组元素。在每一步中，reducer 函数将当前数组值添加到上一步的结果中，直到没有更多元素要添加。

**参数是什么？**

参数是回调函数和可选的初始值。

**回调函数**

preVal：它是前一个回调函数产生的前一个值。

currVal：它是数组的当前元素，reducer 函数会传播它。

currentIndex：当前索引。但是，它是可选的。

arrayToTraverse：要遍历的数组。它也是可选的。

**初始值**

初始值参数是可选的。它是第一次调用回调时，将前一个值初始化的值。如果未指定初始值，则将前一个值初始化为初始值，将当前值初始化为数组中的第二个值。

在某些情况下，Reduce 方法是一种有价值的方法。在某些情况下，它可能会节省你的时间或减少你程序行数。在本文中，我将向你展示 JavaScript 中 reduce() 方法的6个用例。

**1、对数组元素求和**

假设你有以下数组：

```
const prices = [5.99, 2.99, 3.99, 11.59]
```

你可能更喜欢使用 for 循环或 for-each 循环来对上述数组的元素求和，但是，如果使用 reduce()，则可以编写更少的代码。

正如你从介绍中知道的那样，reduce() 接受一个带有4个参数的函数，preVal、currVal、currentIndex、prices，在这种情况下，

你需要传递给 reduce 的第二个参数，是你想要启动的初始值。例如，如果你希望对数组的元素求和，可以将 0 作为初始值。

```
const sum = prices.reduce((preVal, currVal, currentIndex, prices) => {
  return preVal + currVal;
}, 0);
```

reduce() 对数组中的每个元素执行这个函数。第一次执行的 preVal 是你设置为第二个参数的初始值，在本例中为“0”。否则，它将是未定义的。currVal 是数组的第一个元素。对于第二次执行，对数组中的第二个元素执行以下函数：

```
(preVal, currVal, currentIndex, prices) => {
  return preVal + currVal;
}
```

现在，preVal 不是 0。它等于前一次执行中返回的值。所以，preVal = 5.99 + 0。现在，currVal 是第二次迭代的第二个元素。

在这种情况下，你不需要 currentIndex 和prices。因此，你可以将该函数编写为单行函数。

```
const sum = prices.reduce((preVal, currVal) => preVal + currVal, 0);
```

**2、展平数组**

使用reduce()，你可以将多维数组转换为一维数组。

```
var rows = [[2, 3, 5], [1, 2, 4], [8, 5, 5]]
var matrixElements = rows.reduce( function (prev, current) {
  return prev.concat(current);
});
```

**3、创建管道**

此外，你可以减少函数以及数字和字符串。假设你有一系列数学函数。例如，你有以下功能：

```
function increment(input) { return input + 1;}
function decrement(input) { return input - 1; }
function double(input) { return input * 2; }
function halve(input) { return input / 2; }
```

此外，你希望对订单使用 increment、double 和 decrement。因此，你可以创建管道。然后，你可以将它与 reduce() 一起使用。

```

let pipeline = [increment, double, decrement];

const result = pipeline.reduce(function(total, func) {
  return func(total);
}, 8);

// result: 17
```

**4、 从数组中获取对象**

例如，你有一个字符串数组，它们是彩色苹果。使用 reduce() 你可以构造一个苹果对象，如下所示。

```

const apples = ['green', 'red', 'red', 'yellow', 'red', 'yellow', 'green', 'green'];
var appleMap = apples.reduce((prev, apple) => {
  if (prev[apple] >= 1) prev[apple]++;
  else prev[apple] = 1;
  return prev;
}, {});

console.log(appleMap);
// result: {green: 3, red: 3, yellow: 2}
```

**5、找出出现奇数次的整数**

你可以使用 reduce() 来查找在给定数组中出现奇数次的整数。下面的函数有一个不好的地方。如果你给出多个出现奇数次的整数，它将不起作用。

```
const findOdd = (a) => a.reduce((a, b) => a ^ b);
console.log(findOdd([1, 2, 2, 1])); // Result: 0
console.log(findOdd([1, 2, 2, 1, 2, 3, 3])); // Result: 2
console.log(findOdd([1, 2, 3, 4])); // Result: 4 -> Not working
```

**6、求给定数组的最大子数组和**

使用此函数，你可以找到给定数组的最大子数组和。这是一个需要解决的大问题。解决起来并不容易。尤其是想用单线方案来实现这个功能，就更具挑战性了。但是，如果使用reduce() 会更容易。

```
const maxSequence = (a,sum=0) => a.reduce((max,v) => Math.max(sum = Math.max(sum + v, 0), max), 0);
console.log(maxSequence([1,2,3,4])); // Result: 10
console.log(maxSequence([1,2,3,4,-8])); // Result: 10
console.log(maxSequence([1,-2,3,-2,5,-1,3,-9,1,6])); // Result: 8
```

**加餐：reduceRight()**

你也可以使用reduceRight()。它的工作方式与reduce() 相同。但是，它的工作方向相反。当你学习时，reduce() 从第一个元素开始并朝最后一个元素移动。相反，reduceRight() 从最后一个元素开始，然后转到第一个元素。

```

const prices = [5.99, 2.99, 3.99, 11.59];

let sum = prices.reduceRight(function (preVal, currVal) {
    console.log('prev: ', preVal, 'curr: ', currVal);
    return prev + curr;
});
console.log(sum);

// prev:  11.59 curr:  3.99
// prev:  15.58 curr:  2.99
// prev:  18.57 curr:  5.99
// 24.560000000000002
```

**结论**

了解 JavaScript 中一些内置函数的用例可以帮助你提高编码技能。学习用例可以为你提供一些见解，你可以优雅地实现一些功能。

JavaScript 中的 reduce() 也是一个有用的内置函数。如果你知道如何使用它，它是强大的。它可以帮助你编写较少数量的代码行，如汇总价格的示例。

综上所述，本文reduce()的用例如下：

- 对数组元素求和
- 展平数组
- 创建管道
- 从数组中获取对象
- 找出出现奇数次的整数
- 查找给定数组的最大子数组和。