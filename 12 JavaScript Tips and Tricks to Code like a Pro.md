# 12个可以让你像专业人士一样编写JavaScript代码的技巧

英文 | https://medium.com/geekculture/12-javascript-tips-and-tricks-to-code-like-a-pro-1359de0d546a

由于JavaScript是每个 Web 开发人员必须要掌握的技能之一，因此，在本文中，我们将讨论一些专业的JavaScript技巧，它们将节省你的开发时间，并让你感觉自己是一名更加专业的程序员

**1、Quick Console.log**

通过使用以下代码片段，摆脱一遍又一遍地编写 console.log 并使其更短。

```
// Quick Console.log
let c = console.log.bind(document)
c('😄😄😄')
c('This is JavaScript')
c(true)
c(234)
```

**2、箭头函数**

箭头函数技巧将通过缩短函数定义使你的生活更轻松。我主要使用这个技巧来使函数实现更快更容易阅读。下面是两个示例代码。

```

// Arrow Functions
// Example 1
function Print1()
{
  console.log("Hello World") 
}
//arrow function
let Print2 = ()  => {
  console.log("Hello World") 
}
//Example 2
function sum(x, y) 
{
  return x + y
}
//arrow function
let sum2 = (x , y) => { return x + y}
console.log(sum2(3,4)) // 4
```

**3、Spread Operator**

展开运算符是 JavaScript ES6 中运算符集的新增功能。它接受一个可迭代对象（例如数组）并将其扩展为单个元素。下面是扩展运算符使用的示例代码。

```

// Spread Operator
// Array Concatination
let num1 = [1, 2, 3]
let num2 = [4, 5, 6]
let concat = [...num1, ...num2]
console.log(concat) // [1, 2, 3, 4, 5, 6]
// Copying An Array
let alpha = ["a", "b", "c"]
let copy = [...alpha]
console.log(copy) // ["a", "b", "c"]
// Array literals 
let data = [100, 200]
let literal = [...data, 300, 400, 500]
console.log(literal) // [100, 200, 300, 400, 500]
```

**4、Truncating any Array**

你是否知道 length 方法不仅可以显示字符串的大小，还可以将数组截断为任意大小？检查下面的代码示例以了解如何执行此操作。

```

// Truncating an array
let arr = [100, 200, 300, 400, 500, 600]
// make size 3
arr.length = 3
console.log(arr) //[100, 200, 300]
// make size 0
arr.length = 0
console.log(arr) // []
```

**5、Smart Replacing**

这个技巧将通过使用循环替换长字符串数据中的单词来节省你的时间。我们将在 JavaScript 中使用 repac() 方法，它接受两个参数，一个是要替换的单词的正则表达式，第二个是新单词。

当你处理大文本数据并且你用一些新词替换特定词时，这会派上用场。查看下面的代码示例以更好地理解。

```
// Smart Replacing
var str = "This is potato and potato"
console.log(str.replace(/pot/, "tom")) // This is tomato and potato
console.log(str.replace(/pot/g, "tom")) // This is tomato and tomato
```

**6、Numerical Separator**

这个简单的技巧将提高 JavaScript 中大量数据的可读性。我们将使用“_”作为数字分隔符。查看下面的代码示例。

```

// Numerical Separator
// Normal Way
var data1 = 100000
var data2 = 300000000
// With Separator
var data3 = 100_000
var data4 = 300_000_000
console.log(data3) // 100000
console.log(data4) // 300000000
```

**7、Quick Power Calculation**

你可能使用 math.pow() 方法来计算任何数字的幂。这个技巧将使用常规数学方法以快速形式计算功率。

```

// Quick Power Calculation
// Normal Way
console.log(Math.pow(4,5)) // 1024
console.log(Math.pow(2,5)) // 32
// Quick Way
console.log(4**5) //1024
console.log(2**5) // 32\
```

**8、数据转换为数字、字符串、布尔值**

这个很棒的技巧将帮助你将数据转换为数字、字符串和布尔值。在下面的示例中，我展示了如何使用一元运算符将整数转换为字符串。

```

// Convert to Integer
let var1 = 12 + ""
let var2 = 300 + ""
console.log(typeof(var1))  // string
console.log(typeof(var2))  // string
```

这个转换技巧会将你的字符串数字数据转换为整数格式数据。查看下面的代码示例。

```

// Convert to String
let var3 = 14
var3 =+var3
console.log(var3) // 14
console.log(typeof(var3)) // number
```

此转换将向你展示如何将数字或整数转换为布尔格式。下面我展示了一个示例代码供你理解。

```
//Convert Number to Boolean
let var4 = !9
console.log(var4) //false
console.log(typeof(var4))
```

**9、Rest Parameter**

Rest Parameter 语法用于处理函数定义中的无限数量的参数。下面的示例代码将使你了解其余参数的有用性。

```

// Rest Parameter
function sum(...num)
{
  var cal =0; 
  for(const a of num)
  {
    cal +=a
  }
  console.log(cal) //27
}
sum(2, 3, 4, 5, 6, 7)
```

**11、Smart Short Loop**

如果你处理小数据，这个技巧将使你的循环更短。看看下面的代码示例。

```

// Smart Short Loop
const Names = ["Professor", "Tokio", "Denver", "Hesinki"];
// Long version loop
for (let i = 0; i < Names.length; i++) 
{
  console.log( Names[i]);
}
//Short Version Loop
for(let n of Names) console.log(n)
```

**12、解构**

解构是一个 JavaScript 表达式，它允许从数组中解压缩值并将它们绑定到变量。下面的示例代码将向你展示解构的一些用法。

```

// Destructing
// Normal way
function fun()
{ return [2, 4, 6] }
let d = fun()
let x = d[0]
let y = d[1]
let z = d[2]
console.log(x , y, z) // 2  4  6
// destruting way
let [x, y, z] = fun()
console.log(x, y, z) // 2  4  6
// Destructing Swaping
a= 4
b= 2
[a, b] = [b, a] 
console.log(a,b) // 4 2
```

