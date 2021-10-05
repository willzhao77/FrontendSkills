# 我在JavaScript开发项目中使用最多的9种数组方法
英文 | https://javascript.plainenglish.io/9-array-methods-that-i-used-the-most-while-making-20-projects-in-javascript-8aa299eb731

**1、map()**
map() 方法是迄今为止，我最喜欢的 JavaScript 方法。它通过迭代数组的元素并应用所需的数组修改来创建一个新数组。
与 forEach() 方法的回调函数相比，它不会修改原始数组。

```
const foods = ['🍕', '🍔', '🌭', '🍝']
const foodsWithFries = foods.map(food => food + ' 🍟')
console.log(foodsWithFries)
// ['🍕 🍟', '🍔 🍟', '🌭 🍟', '🍝 🍟']const numbers = [1, 2, 3, 4]
const squaredNums = numbers.map(num => num ** 2)
console.log(squaredNums)
 // [1, 4, 9, 16]
```
请注意，这里我使用箭头函数来定义回调函数。可以用多种方式编写相同的函数。
```
// 1. const squaredNums = numbers.map(num => num ** 2)
// 2. const squaredNums = numbers.map(function(num) {    return num ** 2
})
// 3. function square(num) {    return num ** 2
}const squaredNums = numbers.map(square)

```
**2、includes()**
include() 方法在检查数组中是否存在所需元素后返回一个布尔值。
我在使用 API 时大量使用它来检查数组中是否存在某些值。
```
const vehicles = ['🚓', '🛺', '🚑', '🚒']console.log(vehicles.includes('🛺'))
 // trueconsole.log(vehicles.includes('🚜'))
 // false
```
**3、join()**
当我们想使用一些分隔符连接数组的所有元素并返回一个字符串时，我会选择使用 join()。默认分隔符（当你不将任何值作为参数传递时）是逗号 (,)。
```
const animals =['🐇', '🐵', '🐶', '🐴', '🐘']
animals.join()
 // '🐇,🐵,🐶,🐴,🐘'
```
你还可以将自定义分隔符作为参数传递。
```
const animals =['🐇', '🐵', '🐶', '🐴', '🐘']
animals.join(' < ')
 // '🐇 < 🐵 < 🐶 < 🐴 < 🐘'
```
当我想用自定义分隔符在网站上显示数组的元素（使用 DOM 操作）时，我会使用它。
**4、find()**
如果元素满足回调函数中提供的条件，则 find() 方法返回元素的第一个实例。
我用它来检查是否存在任何满足我条件的元素。当没有元素满足条件时，函数返回 undefined。
```
const numbers = [2, 4, 5, 6, 7]
const odd = numbers.find(num => num % 2 !== 0)
console.log(odd)
 // 5const greaterThan12 = numbers.find(num => num > 12)
console.log(greaterThan12)
 // undefined
```
有一个类似的方法 findIndex() ，它返回第一个匹配元素的索引，当没有匹配时，则返回 1。
**5、filter()**
filter() 方法使用满足我们为其指定的条件的元素创建一个新数组。此方法采用回调函数，你必须在其中指定条件。
```
const numbers = [4, 2, 6, 9, 10, 13, 5]
const evenNumber = numbers.filter(num => num % 2 === 0)
console.log(evenNumber)
 // [4, 2, 6, 10]
```
在这里，过滤器方法返回一个新数组，其中包含所有偶数，因为这是我们的条件。
**6、reduce()**
reduce() 方法执行一个 reducer 回调函数。把它想象成当你在现实生活中添加多个数字时。你将从第一个值开始并迭代其他数字，同时，将这些值一个一个地相加。
reduce() 方法做了类似的事情，最后，你会得到一个单一的值。除了添加之外，它还可以执行许多你可能想要的操作。
```
const numbers = [1, 2, 3]
const sum = numbers.reduce( (previousValue, currentValue) => {    return previousValue + currentValue
})
console.log(sum)
 // 6const vegetables = ['🥒', '🥬', '🥕']
const salad = vegetables.reduce((prevVeg, ongoingSalad) => {    return prevVeg + ongoingSalad
})
console.log(salad)
 // 🥒🥬🥕
```
reduce方法不会修改原始数组。
**7、concat()**
concat() 方法用于合并数组。它返回一个全新的数组，而不修改任何提供的数组。
```
const vegetables = ['🍅', '🥦', '🥔', '🧄']
const fruits = ['🍎', '🍉', '🍌']
const food = vegetables.concat(fruits)
console.log(food)
 // ['🍅', '🥦', '🥔', '🧄', '🍎', '🍉', '🍌']

```
我们还可以使用 concat 方法一次性合并多个数组，示例如下：
```
const vegetables = ['🍅', '🥦']
const fruits = ['🍎', '🍉']
const sweets = ['🧁', '🍫', '🍪']
const food = vegetables.concat(fruits, sweets)
console.log(food)
 // ['🍅', '🥦', '🍎', '🍉', '🧁', '🍫', '🍪']

```
**8、slice()**
slice() 方法用于“分割”数组的一部分。它不会更改原始数组并创建该数组的新深层副本。
当你不想更改原始数据而是复制“分割”数组时，这很有用。
```
const emojis = ['😀', '😁', '🙂', '🤩', '😮', '😇', '😆']
emojis.slice(0, 2)
 // ['😀', '😁']emojis.slice(3, 6)
 // ['🤩', '😮', '😇']
```
当我想创建整个数组的深层副本时，我使用 slice 比较实用。通过使用它，我可以放心，我不会修改我的原始数组，并且可以对新数组执行任何操作。
```
const emojis = ['😀', '😁', '🙂']
const emojisCopy = emojis.slice()
emojisCopy.push('🙄')
console.log(emojis)
 // ['😀', '😁', '🙂']console.log(emojisCopy)
  // ['😀', '😁', '🙂', '🙄']
```
我们可以看到原始数组没有被修改。但是，如果我们使用 = 符号来创建新数组，则修改将反映在两个地方，因为它是引用或浅拷贝。
**9、 splice()**
splice() 方法是 JavaScript 中的多种实用程序方法之一。splice 方法的主要目的是从数组中删除元素。但是，你可以单独使用 splice 方法添加、删除和更新元素。
它位于列表末尾的原因是我没有经常使用它，因为它不是很简单。我使用了其他干净且更具可读性的方法来解决相同的问题。
要添加元素，我们需要传递 3 个参数。我们想要插入元素的位置，从该位置开始删除的元素数量，以及要添加的元素的值。
```
const flowers = ['🌻', '🌼', '🌷']
flowers.splice(2, 0, '🌹')
console.log(flowers)
 // ['🌻', '🌼', '🌹', '🌷']// Rose 🌹 added at the 2nd position.
```
当你使用 splice 方法删除元素时，它会返回一个包含这些已删除元素的新数组并修改原始数组。
```
const flowers = ['🌻', '🌼', '🌷', '🌺']
const deletedFlowers = flowers.splice(1, 2, '🌹')
console.log(flowers)
 // ['🌻', '🌹', '🌺']console.log(deletedFlowers)
 // ['🌼', '🌷']
```