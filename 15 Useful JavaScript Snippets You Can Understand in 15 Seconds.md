# 15 个有用的 JavaScript 代码段
英文 | https://levelup.gitconnected.com/15-useful-javascript-snippets-you-can-understand-in-15-seconds-3aa244d9c326

**1、不循环地重复一个字符串**
此 JavaScript 代码段将展示如何在不使用任何循环的情况下重复字符串。我们将通过JavaScript 中的repeat()方法来构建一个数字，该数字将作为你需要的数字副本。

```
//Old Method
for(var i = 0; i<5; i++)
{  
	console.log("😃") // 😃😃😃😃😃
}
// Best Methodconsole.log("😃".repeat(5)) 
//😃😃😃😃😃
```
**2、 数组的差异**
这一个很棒的代码片段，可以帮助你区分数组。当你处理一个长数组并想知道该数组的相似之处或不同之处时，这个会派上用场。
下面的示例代码将帮助你更加清晰理解，你可以在你的JavaScript 项目中自由使用这些代码。
```
//Code Example
function ArrayDiff(a, b)
{  
	const setX = new Set(a)  
	const setY = new Set(b)
	return [    
		...a.filter(x=>!setY.has(x)),    
		...b.filter(x=>!setX.has(x))  
	]
}  
	const Array1 = [1, 2, 3]
  	const Array2 = [1, 2, 3, 4, 5]
console.log(ArrayDiff(Array1, Array2)) // [4, 5]
```
**3、 String 是否为 Json**
当你需要检查数据是字符串，还是 JSON 时，此代码段将派上用场。假设你从服务器端获得响应并解析该数据，你需要检查它是 JSON 还是字符串。下面的代码片段。
```
//Code Example
function isJSON(str){  
    try  
    {      
    	JSON.parse(str)  
    }  
    catch  
    {      
    	return false  
    }
	return true
}
var str = "JavaScript"
console.log(isJSON(str)) //false
```
**4、简短的 Console.log**
厌倦了一遍又一遍地编写 console.log() 吗？不用担心，这个片段会为你节省大量时间来编写长长的 console.log()。
```
var cl = console.log.bind(document)
cl(345) 
cl("JAVASCRIPT")
cl("PROGRAMMING") 
<Give it a try!>
```
**5、全部替换**
此代码段将向你展示如何替换字符串中的单词，而无需迭代每个单词、匹配它并放置新单词。下面的代码片段使用了 replaceAll( Target Word, New Word ) 方法。
```
//Code Examplevar 
str = "Python is a Programming Language, Python is a top programming language and favourite of every developer"
str = str.replaceAll("Python", "JavaScript")
console.log(str) // JavaScript is a Programming Language, JavaScript 5is a top programming language and favourite of every developer
```
**6、将数字转换数字数组**
此代码段可用于将数字转换为数字数组。使用带有 map 的扩展运算符，我们可以在一秒钟内完成此操作。试一试：
```
//example code
const NumberToArray = number => [...`${number}`].map(i => parseInt(i))
console.log(NumberToArray(86734)) //[8,6,7,3,4]
console.log(NumberToArray(1234)) //[1,2,3,4]
console.log(NumberToArray(9000)) //[9,0,0,0]
```
**7、检查数字是否为 2 的幂**
现在，此代码段将帮助你检查是否为 2 的幂。尝试从下面的示例代码中理解它。
```
//example code
const isPowerTwo = n => !!n &&( n & (n  1) ) == 0
console.log(isPowerTwo(3)) //true
console.log(isPowerTwo(8)) //true
console.log(isPowerTwo(4)) //true
```
**8、数字转换为二进制**
此代码段将使用 toString() 方法简单地将数字转换为二进制。看看下面的代码示例。
```
var n1 = 500
console.log(n1.toString(2)) // 111110100
var n2 = 4
console.log(n2.toString(2)) // 100
var n3 = 5004
console.log(n3.toString(2)) // 1001110001100
```
**9、返回数组的幂集**
此代码段将返回你的任何数字数组的 Powerset。检查下面的代码片段以获得更好的理解。

```
//example code
const PowerSet = array => array.reduce((accumalator, current) => accumalator.concat(accumalator.map(n => [current].concat(n))), [[]])
console.log(PowerSet([1,2]))
```
**10、从数组中删除元素**
当你需要从数组中删除元素时，此代码段将派上用场。在下面的代码片段示例中，我们使用了 array.slice() 内置方法。
```
//example code
const DropElement = (array, num = 1) => array.slice(num)
console.log(DropElement([2,45,6,7],2)) //[6, 7]
console.log(DropElement([2,45,6,7],1)) //[45, 6, 7]
```
**11、反转字符串**
现在你不需要循环遍历字符串来反转它。此代码段将展示如何使用扩展运算符 (...) 和 reverse() 函数来反转字符串。
这在反转大字符串时会派上用场，你需要为此提供快速片段代码。检查下面的代码示例。

```
//example code
function Reverse(str){
	return [...str].reverse().join('')
}
console.log(Reverse("data")) //atad
console.log(Reverse("Code")) //edoC
```
**12、深度扁平化阵列**
展平数组是将任何有序数组和二维数组转换为一维数组的过程。简而言之，你可以降低数组的维数。你已经看过 Flatten Array 片段代码，但是深展平数组呢。
当你有一个大的有序数组并且正常的展平对它不起作用时，此代码段非常有用。为此，你将需要一个深展平。

```
//example code
function DeepFlat(array){
	return [].concat(...array.map(value=>  (Array.isArray(value) ? DeepFlat(value) : value)))
}
console.log(DeepFlat([1,[2,[4,6,6,[9]],0,],1])) // [1, 2, 4, 6, 6, 9, 0, 1]
```
**13、计算字节大小**
每个程序员的目标都是让他们的 JavaScript 程序高效并具有良好的性能。为此，我们需要确保我们有一些不会让我们的内存过载的数据大小。查看下面的代码片段以了解如何检查任何数据的字节。
```
// byte size calculation
const ByteSize = string => new Blob([string]).size
console.log(ByteSize("Codding")) // 7 
console.log(ByteSize(true)) // 4
console.log(ByteSize("😄")) // 4
```
**14、数组转为CSV**
CSV 是当今广泛使用的电子表格，你可以使用如下所示的简单代码段将数组转换为 CSV文件。
```
// Code Example
const ArrayToCsv= (array, delimiter =',')=> array.map(value => value.map(num => `"${num}"`).join(delimiter)).join('\n')
console.log(ArrayToCsv([['name', 'age'], ['haider', '22'], ['Peter', '23']]))
// Output
// "name","age"
// "haider","22"
// "Peter","23"
```
**15、数组的最后一个元素**
现在，你不再需要遍历或循环整个数组并提取最后一个元素。你可以使用以下简单的代码片段执行相同的操作。
```
//code example
const LastElement = array => array[array.length  1]
console.log(LastElement([2,3,4])) // 4
console.log(LastElement([2,3,4,5])) // 5
console.log(LastElement([2,3])) // 3
```