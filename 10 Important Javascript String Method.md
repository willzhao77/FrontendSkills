# 10 个重要的 Javascript 字符串方法
英文 | https://osmangoni0827.medium.com/charat-aac315ec813e

**1、charAt()**
这是非常有用的字符串方法。此方法返回字符值。它找出指定的索引形式 Any String。此方法以任意数字为参数。第一个字符的索引为 0。如果没有为 charAt() 提供索引，则默认为 0。

```
Syntax : charAt(index);
Example:let str=`Bangladesh is a popular country`.
console.log(`The character at index 2 is ${sentence.charAt(2)} `)
output: The character at index 2 is n
```
**2、replace()**
replace() 方法返回一个新字符串。它是替换字符串的一部分。

```
Syntax: replace(‘substr’,`newsubstr`);
Example:Let str=’This is osman’;
console.log(str.replace(‘osman’,’kader’));
Result:  This is kader
```
**3、indexOf()**
此方法返回数字值。它是找出任何字符串的索引号。

```
Syntax: concat(str1, str2)
Example:const paragraph =’JavaScript is the world's most popular programming language.’;
const indexOfFirst = paragraph.indexOf(‘language'’);
console.log(indexOfFirst);
Result:50
```
**4、concat()**
```
Syntax: concat(str1, str2)
Example:
let str1=’My name is ‘;
let str2=’Mohammad Osman Goni’;
console.log(concat(str1,str2);
Result: “My name is Mohamad Osman Goni”
```
**5、repeat()**
此方法返回一个新字符串，其中包含给定字符串的指定副本数。
```
Syntax: repeat(count);
Example:
Let str=’Bangladesh’
console.log(str.repeat(3));
Result: ` Bangladesh Bangladesh Bangladesh `
```
**6、split()**
此方法用分隔符分割字符串并返回一个数组。当字符串为空时，split() 方法返回一个包含一个空字符串的数组。
```
Syntax: split(separator)
Example:
let str=’ JavaScript is a text-based programming language used both on the client-side and server-side’;
console.log(str.split(‘ ’);
Result: Array ["JavaScript", "is", "a", "text-based", "programming", "language", "used", "both", "on", "the", "client-side", "and", "server-side"]
```
**7、trim()**
trim() 方法从字符串中删除开头和结尾的所有空白并返回一个新字符串。
```
Syntax: trim()
Example:
const greeting = '   Hello world!   ';
console.log(greeting);
Result: `Hello world`
```
**8、toString()**
此方法将字符串转换为任何对象。它返回一个表示指定对象的字符串。
```
Syntax: toString();
Example:
let str = new String('Hello world');
console.log(str.toString());
Result: `Hello world`;
```
**9、toUpperCase()**
此方法用于将字符串值转换为大写并返回一个新字符串。
```
Syntax: toUpperCase()
Example: let str=` JavaScript allows users to interact with web pages`console.log(str.toUpperCase());
Result : "JAVASCRIPT ALLOWS USERS TO INTERACT WITH WEB PAGES"
```
**10、toLowerCase()**
toLowerCase() 方法用于将任何字符串转换为小写并返回一个新字符串。
```
Syntax: toLowerCase();
Example: let str=’BEYOND WEBSITES AND APPS, DEVELOPERS CAN ALSO USE JAVASCRIPT TO BUILD SIMPLE WEB SERVERS AND DEVELOP THE BACK-END INFRASTRUCTURE USING NODE.JS.’
console.log(str.toLowerCase())
Result: "beyond websites and apps, developers can also use javascript to build simple w
```