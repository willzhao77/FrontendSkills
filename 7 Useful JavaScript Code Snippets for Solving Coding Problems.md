# 7个JavaScript代码片段，可以快速解决你编程中遇到的问题

英文 | https://javascript.plainenglish.io/7-useful-javascript-code-snippets-for-solving-coding-problems-c146e768bb41

**1、数组中的随机项**

要从数组中返回随机项或元素，我们需要使用具有 length 属性的 Math.random() 和 Math.floor() 方法。

下面是一个例子：

```
let cars = ['Ford', 'Ferrari', 'BMW', 'Toyota'];
//Store a random array item in a variable.
let randomCar = cars[Math.floor(Math.random()* cars.length)];
//Print the random item from car array.
console.log(randomCar); //returns random element
```

每当你再次运行代码时，数组中的一个新随机元素就会打印到控制台。

**2、检查参数是否为数字**

在下面的示例中，我们将使用三种方法 isNaN() 、 parseFloat() 和 isFinite() 来检查函数参数是否为数字。

看一看：

```

function isNumber(number){
   return !isNaN(parseFloat(number)) && isFinite(number);
}
isNumber(5); //returns true
isNumber("Hello"); //returns false
```

**3、轻松反转字符串**

为了轻松反转字符串，我们可以使用 reverse() 方法，但它仅适用于数组。这就是为什么我们将使用 split() 将字符串转换为数组，将其反转，然后使用方法 join() 将其转换回字符串。

下面是代码示例：

```

let str = "Hello World";
str.split("").reverse().join(""); //returns 'dlroW olleH'
```

**4、二进制转普通文本**

要使用 JavaScript 将二进制代码转换为普通文本，我们需要先将二进制代码转换为十进制数。然后，我们将使用 String.fromCharCode() 方法将小数转换为文本。

下面是一个例子：

```
function binaryToText(binary) {
//Convert binary into an array of strings separated by whitespace.    binary = binary.split(' ');
//convert from binary to decimals to text. 
return binary.map(elem => String.fromCharCode(parseInt(elem, 2))).join("");
}
binaryToText("01001001 00100000 01101100 01101111 01110110 01100101 00100000 01001010 01100001 01110110 01100001 01010011 01100011 01110010 01101001 01110000 01110100"); //returns I love JavaScript
binaryToText("01010100 01101000 01100001 01110100 00100111 01110011 00100000 01100111 01101111 01101111 01100100"); //returns That's good
```

**5、计算一个数的阶乘**

为了计算一个数的阶乘，我们将使用带有三元运算符的箭头函数。就像你在下面的例子中看到的那样：

```

const getFactorial = num =>
 num < 0 ?
 (()=>{
   throw new TypeError('No negative numbers');
 })()
 : num <= 1
  ? 1
  : num * getFactorial(num - 1);
//examples:
getFactorial(0); //returns 1
getFactorial(5); //returns 120
```

**6、从数组中返回最小值和最大值**

通过使用带有扩展运算符的 Math.max() 和 Math.min() 方法。我们可以轻松地从数字数组中获取最大和最小数字。

下面是代码示例：

```

let nums = [67, 99, 4, 2, 77];
//minimum number
Math.min(...nums); //returns 2
//maximum number
Math.max(...nums); //returns 99
```

**7、检查性能**

如果你想检查一段代码运行和执行需要多长时间，你可以像我们在下面的例子中那样使用 performance.now() 方法：

```
var start = performance.now();
//Your piece of code starts here
for(let i = 0; i < 100; i++){
 console.log(i);
}
//Your piece of code ends here
var duration = performance.now() - start;
console.log(duration); //54.89999961853027
```

