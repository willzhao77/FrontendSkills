# 30+实用的JavaScript 开发技巧，立刻提升你的工作效率

英文 | https://javascript.plainenglish.io/35-javascript-short-hands-coding-methodologies-28ea2d7d0a5e

**1、声明变量**
在函数的开头声明赋值变量是一种很好的做法。在同时声明多个变量时，这种速记方法可以为你节省大量时间和空间。
不友好写法：

```
let x;let y;let z = 3;
```
友好写法：
```
let x, y, z=3;
```
**2、使用三元运算符**
当你开始使用三元条件而不是使用 if...else 语句时，你的生活会变得更轻松。
不友好写法：
```
const age = 26;let eligibility;if(age > 18){  eligibility = "Allowed";}else{  eligibility = "Not Allowed";}
```
友好写法：
```
let eligibility = (age > 18) ? "Allowed" : "Not Allowed";
```
你还可以像这样嵌套 if 语句：
```
let eligibility = age > 10 ? "greater than 10" : (age < 5 ? "less than 5" : "between 5 and 10");
```
**3、JavaScript For 循环**
如果你想要纯JavaScript 并且不想依赖诸如 jQuery 或 lodash 之类的外部库，那么这个小技巧非常有用。
不友好写法：
```
const fruits = ['mango', 'peach', 'banana'];for (let i = 0; i < fruits.length; i++)
```
友好写法：
```
for (let fruit of fruits)
```
如果你只想访问索引，请执行以下操作：
```
for (let index in fruits)
```
如果你想访问文字对象中的键，这也适用：
```
const obj = {continent: 'Africa', country: 'Kenya', city: 'Nairobi'}for (let key in obj)  console.log(key) // output: continent, country, city
```
Array.forEach 的简写：
```
function logArrayElements(element, index, array) {  console.log("a[" + index + "] = " + element);}[5, 7, 2].forEach(logArrayElements);// a[0] = 5// a[1] = 7// a[2] = 2
```
**4、数组查找**
如果你曾经负责用纯 JavaScript 编写 find 函数，你可能会使用 for 循环。在 ES6 中，引入了一个名为 find() 的新数组函数。
不友好写法：
```
const pets = [  { type: 'Dog', name: 'Max'},  { type: 'Cat', name: 'Karl'},  { type: 'Dog', name: 'Tommy'},]function findDog(name) {  for(let i = 0; i<pets.length; ++i) {    if(pets[i].type === 'Dog' && pets[i].name === name) {      return pets[i];    }  }}
```
友好写法：
```
pet = pets.find(pet => pet.type ==='Dog' && pet.name === 'Tommy');console.log(pet); // { type: 'Dog', name: 'Tommy' }
```
**5、If Presence**
这可能是微不足道的，但值得一提。在进行“if 检查”时，有时可以省略赋值运算符。
不友好写法：
```
if (isLovely === true)
```
友好写法：
```
if (isLovely)
```
另外，请注意，这两个示例并不完全相等，因为只要 isLovely 是一个真值，它检查就会通过。
这是另一个例子。如果 a 不等于 true，则执行某些操作。
不友好写法：
```
let a;if ( a !== true ) {// do something...}
```
友好写法：
```
let a;if ( !a ) {// do something...}
```
**额外加餐：格式化 JSON 代码**
当你想在不使用任何第三方工具的情况下格式化 JSON 对象或 JSON 响应时。打开你的浏览器控制台并点击以下命令来格式化你的JSON。
stringify 方法接受三个输入。值、替换器和空间。也许，你只知道价值！
接下来的两个是可选参数。这就是为什么我们没有以一般方式使用它们。要缩进我们的 JSON，我们必须使用 space 参数。
```
console.log(JSON.stringify({name:"Rax",Age:26},null,'\t'));
```
**6、 箭头函数**
经典函数以其简单的形式易于阅读和编写，但是一旦你开始将它们嵌套在其他函数调用中，它们就会变得有点冗长和混乱。
不友好写法：
```
function sayHi(name) {  console.log('Hello Rax', name);}setTimeout(function() {  console.log('Loaded')}, 2000);list.forEach(function(item) {  console.log(item);});
```
友好写法：
```
sayHi = name => console.log('Hello Rax', name);setTimeout(() => console.log('Loaded'), 2000);list.forEach(item => console.log(item));
```
需要注意的是，箭头（类似于 Java Lambda 表达式）函数中 this 的值与普通函数的确定方式不同，因此，这两个示例并不严格等效。
**7、多行字符串**
如果你发现自己需要在代码中编写多行字符串，你可以这样编写：
不友好写法：
```
const lorem = 'Lorem ipsum dolor sit amet, consectetur\n\t'    + 'adipisicing elit, sed do eiusmod tempor incididunt\n\t'    + 'ut labore et dolore magna aliqua. Ut enim ad minim\n\t'    + 'veniam, quis nostrud exercitation ullamco laboris\n\t'    + 'nisi ut aliquip ex ea commodo consequat. Duis aute\n\t'    + 'irure dolor in reprehenderit in voluptate velit esse.\n\t'
```
但是，有一个更简单的方法。只需使用反引号` ...`。
友好写法：
```
const lorem = `Lorem ipsum dolor sit amet, consectetur    adipisicing elit, sed do eiusmod tempor incididunt    ut labore et dolore magna aliqua. Ut enim ad minim    veniam, quis nostrud exercitation ullamco laboris    nisi ut aliquip ex ea commodo consequat. Duis aute    irure dolor in reprehenderit in voluptate velit esse.`
```
**8、模板文字**
你是否厌倦了使用 ' + ' 将多个变量连接成一个字符串？难道没有更简单的方法来做到这一点吗？如果你能够使用 ES6，那么，你很幸运。你需要做的就是使用反引号和 ${} 来包含你的变量。
不友好写法：
```
const welcome = 'You have logged in as ' + firstName + ' ' + lastName + '.'const db = 'http://' + host + ':' + port + '/' + database;
```
友好写法：
```
const welcome = `You have logged in as ${firstName} ${lastName}`;const db = `http://${host}:${port}/${database}`;
```
**9、十进制指数**
你可能已经看到了这个。它本质上是一种不带尾随零的数字书写方式。例如，1e5 实质上意味着 1 后跟 5 个零。它表示一个等于 1,00,000 的十进制基数（JavaScript 将其解释为浮点类型）。
不友好写法：
```
for (let i = 0; i < 10000; i++) {}
```
友好写法：
```
for (let i = 0; i < 1e7; i++) {}// All the below will evaluate to true1e0 === 1;1e1 === 10;1e2 === 100;1e3 === 1000;1e4 === 10000;1e5 === 100000;
```
**10、短路评估**
如果预期的参数为空或未定义，则无需编写五六行代码来分配默认值，我们可以简单地使用短路逻辑运算符并仅用一行代码完成相同的事情。
不友好写法：
```
let dbHost;if (process.env.DB) {  dbHost = process.env.DB;} else {  dbHost = '127.0.0.1';}
```
友好写法：
```
const dbHost = process.env.DB || '127.0.0.1';
```
**加餐：获取数组中的最后一项**
如果你想从数组的末尾取元素，你可以使用带有负整数的切片方法。
```
let array = [0, 1, 2, 3, 4, 5, 6, 7] console.log(array.slice(-1));>>>[7]console.log(array.slice(-2));>>>[6, 7]console.log(array.slice(-3));>>>[5, 6, 7]
```
**11、对象属性**
在 JavaScript 中定义对象字面量让生活变得更轻松。ES6 提供了一种更简单的方法来为对象分配属性。如果变量名称与对象键相同，则可以利用速记符号。
不友好写法：
```
const x = 2020, y = 2021;const obj = { x:x, y:y };
```
友好写法：
```
const obj = { x, y };
```
**12、隐式回报**
return 是我们经常使用的关键字，用于返回函数的最终结果。带有单个语句的箭头函数将隐式返回其计算结果（该函数必须省略大括号 ({}) 以省略 return 关键字）。
要返回多行语句（例如对象字面量），必须使用 () 而不是 {} 来包装函数体。这确保代码被评估为单个语句。
不友好写法：
```
function calcCircumference(diameter) {  return Math.PI * diameter}
```
友好写法：
```
calcCircumference = diameter => (  Math.PI * diameter;)
```
**13、解构赋值**
如果你正在使用任何流行的 Web 框架，你很有可能会使用对象文字形式的数组或数据在组件和 API 之间传递信息。一旦数据对象到达一个组件，你就需要解压它。
不友好写法：
```
const observable = require('mobx/observable');const action = require('mobx/action');const runInAction = require('mobx/runInAction');const store = this.props.store;const form = this.props.form;const loading = this.props.loading;const errors = this.props.errors;const entity = this.props.entity;
```
友好写法：
```
import { observable, action, runInAction } from 'mobx';const { store, form, loading, errors, entity } = this.props;
```
你甚至可以分配自己的变量名称：
```
const { store, form, loading, errors, entity:contact } = this.props;
```
大多数情况下，Visual Studio 代码编辑器提供用于自动导入或自动完成的插件。
**14、展开运算符**
ES6 中引入的扩展运算符有几个用例，可以使 JavaScript 代码使用起来更加高效和有趣。它可用于替换某些数组函数。展开运算符是用三个点表示的。
不友好写法：
```
// joining arraysconst odd = [1, 3, 5];const nums = [2 ,4 , 6].concat(odd);// cloning arraysconst arr = [1, 2, 3, 4];const arr2 = arr.slice()
```
友好写法：
```
// joining arraysconst odd = [1, 3, 5 ];const nums = [2 ,4 , 6, ...odd];console.log(nums); // [ 2, 4, 6, 1, 3, 5 ]// cloning arraysconst arr = [1, 2, 3, 4];const arr2 = [...arr];
```
与 concat() 函数不同，你可以使用扩展运算符在另一个数组内的任何位置插入一个数组。
```
const odd = [1, 3, 5 ];const nums = [2, ...odd, 4 , 6];
```
你还可以将扩展运算符与 ES6 解构符号结合使用：
```
const { a, b, ...z } = { a: 1, b: 2, c: 3, d: 4 };console.log(a) // 1console.log(b) // 2console.log(z) // { c: 3, d: 4 }
```
**15、默认参数值**
你可以使用 if 语句来定义函数参数的默认值。在 ES6 中，你可以在函数声明本身中定义默认值。
不友好写法：
```
function volume(l, w, h) {  if (w === undefined)    w = 3;  if (h === undefined)    h = 4;  return l * w * h;}
```
友好写法：
```
volume = (l, w = 3, h = 4 ) => (l * w * h);volume(2) //output: 24
```
**加餐：截断数组**
如果你想破坏性地从数组末尾删除值，有比使用 splice() 更快的替代方法。
例如，如果你知道原始数组的大小，则可以重新定义其长度属性，如下所示：
```
let array = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];array.length = 4;console.log(array); // Result: [0, 1, 2, 3]
```
这是一个特别简洁的解决方案。但是，我发现 slice() 方法的运行时间更快。如果速度是你的主要目标，请考虑使用以下内容：
```
let array = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];array = array.slice(0, 4);console.log(array); // Result: [0, 1, 2, 3]
```
**16、Object [key] 好处**
你知道 Foo.bar 也可以写成 Foo['bar'] 吗？起初，你似乎没有理由这样写。但是，这种表示法为你提供了编写可重用代码的构建块。
考虑这个验证函数的简化示例：
```
function validate(values) {  if(!values.first)    return false;  if(!values.last)    return false;  return true;}console.log(validate({first:'Bruce',last:'Wayne'})); // true
```
这个函数完美地完成了它的工作。但是，请考虑一个场景，你有很多表单需要应用验证，但具有不同的字段和规则。构建一个可以在运行时配置的通用验证函数不是很好吗？
```
// object validation rulesconst schema = {  first: {    required:true  },  last: {    required:true  }}// universal validation functionconst validate = (schema, values) => {  for(field in schema) {    if(schema[field].required) {      if(!values[field]) {        return false;      }    }  }  return true;}console.log(validate(schema, {first:'Bruce'})); // falseconsole.log(validate(schema, {first:'Bruce',last:'Wayne'})); // true
```
现在我们有了一个验证函数，我们可以在所有表单中重用，而无需为每个表单编写自定义验证函数。
**17、指数幂**
它对数学指数幂函数很有用：
不友好写法：
```
Math.pow(2,3); // 8Math.pow(2,2); // 4Math.pow(4,3); // 64
```
友好写法：
```
2**3 // 82**4 // 44**3 // 64
```
**18、将字符串转换为数字**
有时你的代码会接收到字符串格式的数据，但需要以数字格式进行处理。这没什么大不了的，我们可以进行快速转换。
不友好写法：
```
const num1 = parseInt("100");const num2 =  parseFloat("100.01");
```
友好写法：
```
const num1 = +"100"; // converts to int data typeconst num2 =  +"100.01"; // converts to float data type
```
**19、Object.entries()**
这是 ES8 中引入的一项功能，允许你将文字对象转换为键/值对数组。请参阅下面的示例：
```
const credits = { producer: 'John', director: 'Jane', assistant: 'Peter' };const arr = Object.entries(credits);console.log(arr);/** Output:[ [ 'producer', 'John' ],  [ 'director', 'Jane' ],  [ 'assistant', 'Peter' ]]**/
```
**20、Object.values()**
这也是 ES8 中引入的一个新特性，它执行类似于 Object.entries() 的功能，但没有关键部分：
```
const credits = { producer: 'John', director: 'Jane', assistant: 'Peter' };const arr = Object.values(credits);console.log(arr);/** Output:[ 'John', 'Jane', 'Peter' ]**/
```
**加餐：使用 === 而不是 ==**
==（或 !=）运算符在需要时执行自动类型转换。===（或 !==）运算符不会执行任何转换。它比较值和类型，这可以被认为比 == 更快。
```
[10] === 10    // is false[10]  == 10    // is true'10' == 10     // is true'10' === 10    // is false []   == 0     // is true [] ===  0     // is false '' == false   // is true but true == "a" is false '' ===   false // is false
```
另外，请注意，undefined、null、0、false、NaN、''（空字符串）都是假的。
**21、按位索引**
使用数组执行查找时，indexOf() 函数用于检索你要查找的项目的位置。如果未找到该项目，则返回值 -1。在 JavaScript 中，0 被认为是“假的”，而大于或小于 0 的数字被认为是“真”的。因此，必须像这样编写正确的代码。
不友好写法：
```
if(arr.indexOf(item) > -1) { // Confirm item IS found}if(arr.indexOf(item) === -1) { // Confirm item IS NOT found}
```
友好写法：
```
if(~arr.indexOf(item)) { // Confirm item IS found}if(!~arr.indexOf(item)) { // Confirm item IS NOT found}
```
按位（~）运算符将返回除 -1 以外的任何值的真值。否定它就像！~一样简单。或者，我们也可以使用 includes() 函数：
```
if(arr.includes(item)) { // Returns true if the item exists, false //if it doesn't}
```
**22、对象属性赋值**
考虑以下代码：
```
let fname = { firstName : 'Black' };let lname = { lastName : 'Panther'}
```
你如何将它们合并为一个对象？一种方法是编写一个函数，将数据从第二个对象复制到第一个对象上。不幸的是，这可能不是你想要的——你可能需要创建一个全新的对象而不改变任何现有对象。最简单的方法是使用 ES6 中引入的 Object.assign 函数：
```
let full_names = Object.assign(fname, lname);
```
你还可以使用 ES8 中引入的对象销毁符号：
```
let full_names = {...fname, ...lname};
```
你可以合并的对象属性数量没有限制。如果你确实有具有相同属性名称的对象，则值将按照它们合并的顺序被覆盖。
**23、Double Bitwise NOT 速记**
按位运算符是你在 JavaScript 初学者教程中学到的功能之一，而且，你永远无法在任何地方实现它们。同意吗？此外，如果你不处理二进制，谁愿意使用 1 和 0？
然而，双位非运算符有一个非常实用的用例。你可以将其用作 Math.floor() 的替代品。Double Bitwise NOT 运算符的优点是它执行相同操作的速度要快得多。您可以在此处阅读有关按位运算符的更多信息。
不友好写法：
```
Math.floor(4.9) === 4  //true
```
友好写法：
```
~~4.9 === 4  //true
```
**24、短路评估**
将变量值分配给另一个变量时，你可能希望确保源变量不为空、未定义或为空。你可以编写带有多个条件的长 if 语句，也可以使用短路评估。
不友好写法：
```
if (variable1 !== null || variable1 !== undefined || variable1 !== '') {     let variable2 = variable1;}
```
友好写法：
```
const variable2 = variable1  || 'new';
```
不相信我？自行测试（在es6console中粘贴以下代码）：
```
let variable1;let variable2 = variable1  || 'bar';console.log(variable2 === 'bar'); // prints truevariable1 = 'foo';variable2 = variable1  || 'bar';console.log(variable2); // prints foo
```
请注意，如果将 variable1 设置为 false 或 0，将分配值栏。
**25、强制参数**
默认情况下，如果未传递值（简而言之，未分配任何值），JavaScript 会将函数参数设置为 undefined。其他一些语言会抛出警告或错误。要强制参数分配，你可以使用 if 语句在未定义时抛出错误，或者你可以利用“强制参数速记”。
不友好写法：
```
function foo(bar) {  if(bar === undefined) {    throw new Error('Missing parameter!');  }  return bar;}
```
友好写法：
```
mandatory = () => {  throw new Error('Missing parameter!');}foo = (bar = mandatory()) => {  return bar;}
```
**加餐：交换两个变量**
为了交换两个变量，我们经常使用第三个变量。但是它可以通过数组解构赋值轻松完成。
不友好写法：
```
let x = "rakshit", y = "shah";const temp = x;x = y;y = temp;
```
友好写法：
```
[x,y] = [y,x]
```
**26、将任何东西转换为布尔值**
在开发任何代码时，你可能会遇到需要布尔值来比较或进行真/假检查的情况。这种方法在这种情况下会很有用！
```
const foo = 'some string lines';const toBool = !!fooconsole.log(toBool) // true
```
**27、 将任何东西转换为数字**
通过使用 + 运算符，你可以实现它。
```
const foo = '522'const toNumber = +fooconsole.log(toNumber) // 522const toNegativeNumber = -fooconsole.log(toNegativeNumber) // -522
```
**28、将数组转换为对象**
```
const arr = [ 'foo', 'bar', 1]const obj = { ...arr }console.log(obj) // {0: "foo", 1: "bar", 2: 1}
```
**29、删除Array中的重复项**
Set 对象允许你存储任何类型的唯一值，无论是原始值还是对象引用。
```
const arr = ['a', 'b', 'c', 'b', 'd']const newArr = [... new Set(arr)]console.log(newArr) // ["a", "b", "c", "d"]
```
**30、经常注释你的代码**
通常，开发人员讨厌或忘记为他们开发的函数、算法或代码添加注释。显然，如果你在需要的地方发表评论，这将对你的同行有所帮助。
注释是总结代码片段目的的好方法，可以为你的开发伙伴节省自行确定它所需的时间。
如果代码没有完成，它被注释成完成的任务，它还允许他们捕捉可能的错误。一般来说，最好对每个功能都留下一个注释。
如果你不确定是否应该发表评论，那就去做吧！如果它太杂乱，以后可以随时删除。
当你觉得有些代码缺失或需要在未来完成时，只需添加 TODO 注释即可。
```
//declares and initializes var x<script>var x = 5;//TODO: Add a function to find factorial of value x.</script>
```