# 8个常用的JavaScript数组方法每个开发人员都必须知道
英文 | https://javascript.plainenglish.io/array-methods-that-every-javascript-developer-must-know-3aa311e15a66

数组是程序员最常用的东西之一。在本文中，我将介绍重要的 JavaScript 数组方法，这些方法将帮助你提升工作效率，同时，也会让你作为开发人员的生活变得更加轻松。作为示例，我将使用 student 对象的 student 数组来处理所有这些不同的数组方法。

```
const students = [  {name: "sam", age: 26, score: 80},  
    {name: "john", age: 25, score: 86},  
    {name: "dean", age: 20, score: 78},  
    {name: "timothy", age: 18, score: 95},  
    {name: "frank", age: 21, score: 67}
    ]
```
现在，让我们开始吧。
**1、filter()**
现在，我们假设，我们想要得到这个列表中年龄小于或等于 24岁的所有学生。我们需要使用filter方法来过滤掉所有大于 24 岁的学生。
```
const students = [  
    {name: "sam", age: 26, score: 80},  
    {name: "john", age: 25, score: 86},  
    {name: "dean", age: 20, score: 78},  
    {name: "timothy", age: 18, score: 95},  
    {name: "frank", age: 21, score: 67}
] 
const filteredStudents = students.filter((students) => {  
    //this filter method just takes a single function, which is going to have one parameter of   student   which is every student/item in the array  
    // we'd need to return a true or false statement on whether or not we want to include them in the   new array  
	return students.age <= 24  //This line basically stashes all of the students whose ages are less than a 24 in the new   filteredStudents array
})

console.log(filteredStudents)

//
```
这种filter()数组方法超级好用。你所做的就是为每个项目返回 true 或 false。如果为真，则将其添加到新数组中，如果为假，则不添加。filter 方法和本文中所有其他方法的优点在于，它们实际上不会更改你正在过滤的底层对象，因此我们可以记录学生数组，并且它仍然包含所有项目。这非常方便，因为我们在使用这些新数组方法创建新数组时，不必担心更改旧数组。
**2、map()**
map() 允许你获取一个数组并将其转换为一个新数组。在这个中，新数组中的所有项目看起来都略有不同。如果我们想得到每个学生的名字。我们可以通过使用 map() 获取名称数组。
```
 const students = [  
     {name: "sam", age: 26, score: 80},  
     {name: "john", age: 25, score: 86},  
     {name: "dean", age: 20, score: 78},  
     {name: "timothy", age: 18, score: 95},  
     {name: "frank", age: 21, score: 67}
 ] 
const studentNames = students.map((students) => {
    //the method takes a single function, with the students/items as a parameter
    // here we just return what we want in the new array

    return students.name

    })
	console.log(studentNames)
/*If we print out these student names,console.log(studentNames)we get a new array that is just full of all the different names of the students.*/
                                                  /******************/
```
这可以通过数组中的任何内容来完成。例如，当你想要获取一个对象，并且只获取名称或单个键，或者获取一个数组并将其转换为另一个数组时，该方法非常有用。此方法是 JavaScript 数组中最流行的方法之一。
**3、find（）**
此方法允许你在数组中查找单个对象。这是直截了当的方法。假设我们想找到一个名叫 john 的学生。
```
const students = [  
    {name: "sam", age: 26, score: 80},  
    {name: "john", age: 25, score: 86},  
    {name: "dean", age: 20, score: 78},  
    {name: "timothy", age: 18, score: 95},  
    {name: "frank", age: 21, score: 67}
] 
const singleStudent = students.find((students) => {
return students.name === 'john'
})

console.log(singleStudent)

/*  console.log(singleStudent) will give the everything associated with john in this example, I.e   Object {    age: 25,    name: "john",    score: 86  }
*/
```
在这个方法中，逻辑是有一个 true 或 false 语句，它将返回第一个计算结果为 true 的数组项。

**4、forEach()**
与其他方法不同， forEach() 实际上不返回任何内容，因此不需要 return 语句。假设我们需要打印出 student 数组中所有学生的名字，我们会这样做：

```
const students = [  
    {name: "sam", age: 26, score: 80},  
    {name: "john", age: 25, score: 86},  
    {name: "dean", age: 20, score: 78},  
    {name: "timothy", age: 18, score: 95},  
    {name: "frank", age: 21, score: 67}
] 

students.forEach((students) => {
	console.log(students.name
	)})
/*  the result is the name property printed out on the console line after line like so
  
  "sam"  
  "john"  
  "dean"  
  "timothy"  
  "frank"
  */
```
这将与 for 循环非常相似，但它将采用一个函数。因此，对于每个数组项，它将执行函数内的代码块。
这种方法只是使处理需要循环项目的数组变得更加容易，因为你不必像通常那样写出笨重而长的for循环语句。

**5、some（）**
这个方法与我们的大多数其他函数有点不同，它不是返回一个全新的数组，而是返回 true 或 false。所以我们可以检查这个数组中是否有一些学生是未成年人。

```
const students = [  
    {name: "sam", age: 26, score: 80},  
    {name: "john", age: 25, score: 86}, 
    {name: "dean", age: 20, score: 78},  
    {name: "timothy", age: 18, score: 95},  
    {name: "frank", age: 21, score: 67}
] 

const hasUnderageStudents = students.some((students) => {
	return students.age < 18
})

console.log(hasUnderageStudents)

/*  
this will return false because there is no underage student in the array.
*/
```
因此，如果任何学生项目的年龄值低于 18，该函数将返回 true。该方法只是检查数组中是否有任何内容返回 true，如果是，则整个内容返回 true。
**6、every()**
此方法与 some() 非常相似，除了检查至少一项以评估为真或假之外，它会检查以确保每一项都符合给定的条件。
如果我使用 some() 代码示例中使用的相同代码。
```
const students = [  
    {name: "sam", age: 26, score: 80},  
    {name: "john", age: 25, score: 86},  
    {name: "dean", age: 20, score: 78},  
    {name: "timothy", age: 18, score: 95},  
    {name: "frank", age: 21, score: 67}
] 

const hasUnderageStudents = students.every((students) => {
	return students.age < 18
})

console.log(hasUnderageStudents)
// this returns false because there are no ages below 18
```
如果我要将条件更改为每个项目评估为真的条件，则整个事情都会返回真。
```
const students = [  
    {name: "sam", age: 26, score: 80},  
    {name: "john", age: 25, score: 86},  
    {name: "dean", age: 20, score: 78},  
    {name: "timothy", age: 18, score: 95},  
    {name: "frank", age: 21, score: 67}
] 
const hasUnderageStudents = students.every((students) => {  
	return students.age < 40
	})
	
console.log(hasUnderageStudents)
// this will return true because every single age property is below 40
```
**7、reduce()**
此方法与所有其他方法完全不同，因为它实际上是对数组进行一些操作并返回所有这些不同操作的组合。
假设我想要学生数组中所有项目的总分，通常会进行 for 循环并每次都将分数相加，在循环结束时，将打印出总分。为了避免冗长的过程，你可以使用 reduce() 方法来执行此操作。
简化方法的语法与其他方法不同。它不是采用数组本身，而是采用一个数组和一个属性，用于我们想要将所有内容减少到和在我们的示例中的分数。除了函数之外，它还需要第二个参数，这将是你的起点，在我们的例子中，我们希望从零开始我们的总数。
```
const students = [  
    {name: "sam", age: 26, score: 80},  
    {name: "john", age: 25, score: 86},  
    {name: "dean", age: 20, score: 78},  
    {name: "timothy", age: 18, score: 95},  
    {name: "frank", age: 21, score: 67}
] 

const totalScore = students.reduce((currentTotal, students) => {
	return students.score + currentTotal
	}, 0)
	
console.log(totalScore)
```
在代码读取时，我们有 reduce() 方法，该方法对数组中的每一项运行一个函数。
该函数的第一个参数将是该数组的前一次迭代返回的任何内容，第二个参数是数组中的实际项目。
currentTotal 将在第一次迭代时开始，使用我们作为 reduce() 方法的第二个参数传入的任何内容，在我们的例子中为零。
这个 reduce() 方法第一次运行，所以我们得到零和“sam”项。所以它只是做了80 加零并返回那个值，也就是 80。
该方法第二次运行时，返回值 80 成为当前总数，我们的下一项是 'john'，所以它计算了 86 加上我们当前的总数 80，即 166，并将其放回当前总数。它一直这样做，直到我们到达数组中的最后一个项目，该项目将作为 totalScore 变量中的总数输出。
这种方法有点混乱，但是，当你需要对数组中的所有项目进行某种累积操作时，它非常有用，例如，获取所有项目的总价，每日股票价格等。
**8、includes()**
此方法不接受函数作为参数。它需要一个参数。它通常用于不需要大量繁重操作的简单数组中。假设你有一堆水果，
const Fruits = [ 'mango', 'apple', 'orange', 'pineapple', 'lemon']
contains() 方法实现的是一种简单方法，是检查某个水果是否在数组中。
```
const fruits = [ 'mango', 'apple', 'orange', 'pineapple', 'lemon']

const includesApple = fruits.includes('apple')

console.log(includesApple) // this will return true because 'apple' is one of the items inside the array.
```
在我看来，这些方法是任何 JavaScript 开发人员都必须知道的，因为数组是最常用于组织的数据结构之一。掌握好这些方法将大大提高你在阵列方面的技能和解决问题的能力。
如果你觉得今天的内容对你有用，清请记得分享给你身边的开发者朋友们。
感谢你的阅读，祝编程愉快！