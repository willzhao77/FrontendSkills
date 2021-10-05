# 10条可以写出漂亮JavaScript 代码的样式规则

英文 | https://javascript.plainenglish.io/javascript-aesthetics-101-style-rules-for-beautiful-code-9d25642512d

你知道为什么很多人讨厌PHP吗？这主要是因为它的外观。PHP 跟像你想象的一样丑陋。因为 PHP 的创建者没有为 PHP 建议任何大小写或格式。一些开发人员使用 under_score，而其他开发人员使用 PascalCase。

因此，这种不一致最终引起了人们对 PHP 的巨大仇恨。

幸运的是，JavaScript 并非如此，因为编写 JavaScript 代码有一些官方规则。例如，camelCase 是官方建议的 JavaScript 大小写方法。但是，由于以下原因，将这些样式规则提升到一个新的水平并为 JavaScript 创建一个通用的视觉效果至关重要：

在整个代码库中拥有一致的风格使其易于阅读和更改。

当另一个 JavaScript 开发人员查看你编写的代码时，他/她不会感到不舒服，因为一切都很熟悉。

随着项目的进行以及你编写的代码越多，如果没有样式指南，维护和改进就会变得更加困难。

所以，这里是我在 Airbnb 的 JavaScript 风格指南中的首选。使用这些规则将使你的代码更具可读性和一致性。此外，你编写的代码可以在 4 个月内被其他开发人员甚至你轻松阅读。

以下就是我列举的10条编写漂亮JavaScript代码的规则。

**1、对变量声明使用 Let 和 Const**

在 ES2015 中引入了 let 和 const 关键字，它们用于替换 var。但是 var 有什么问题呢？嗯，很多。

var 从一开始就在JavaScript 中，但它对今天的标准有一些缺点。它是提升和功能范围的，随着项目的发展，这会导致全球范围内的意外行为和污染。例如，由于 var 不是块范围的，它也在块级标记之外定义，例如 if 和 for。例如，迭代变量 i 是在循环完成后定义的。

```

var a = 1; // bad
let a = 1; // good

// const and let only exist in the blocks they are defined in.
{
  let a = 1;
  const b = 1;
  var c = 1;
}
console.log(a); // ReferenceError
console.log(b); // ReferenceError
console.log(c); // Prints 1
```

**2、尽可能使用隐式构造函数**

如果你正在使用 JavaScript，你应该知道有多种方法可以完成相同的任务。例如，你可以使用三元组或 if-else 块来创建条件逻辑。这种多样化的选择有时会导致你编写的代码不一致。

要创建空对象，你可以使用 Object 构造函数或隐式 {}。对于字符串、函数、数组、数字等，情况也是如此。为了在阅读中保持一致性和易用性，请尽可能使用隐式构造函数。

```

// bad

const a = new Object(); 
const b = new String("str");
const c = new Function('a', 'b', 'return a + b');

// good

const a = {};
const b = "str";
const c = (a,b) => a + b;
```

**3、字符串优先使用单引号**

为了保持一致性，在所有代码库中使用单引号 ' 代替双引号 " 和模板文字（反引号）`。为了简化这个过程，你可以利用 Prettier 立即格式化。

```

// bad
const name = "Edmon Dantès";

// bad - template literals should contain interpolation or newlines
const name = `Edmon Dantès`;

// good
const name = 'Edmon Dantès';
```

**4、尽可能使用字符串插值**

在 JavaScript 中，正如我所提到的，有很多方法可以获得相同的结果，但其中一些方法比其他方法更复杂。要连接字符串，你可以使用 + 运算符、数组上的 join 方法或字符串上的 concat 方法。然而，使用模板文字是完成这项任务最复杂和最简单的方法。

```

// bad
const str = 'How are you, ' + name + '?';

// bad
const str = ['How are you, ', name, '?'].join();

// good
const str = `How are you, ${name}?`;
```

```
const str = `How are you, ${name}?`;
```

**5、选择命名函数表达式**

通常，每个人都有自己喜欢的方法来创建函数，因为 JavaScript 在方法方面非常慷慨。有箭头函数、匿名函数表达式、函数声明等。但是要编写一致且可读的 JavaScript 代码，你应该到处使用一种类型。

使用命名函数表达式而不是声明具有一些关键优势。函数表达式没有被提升，这意味着使用一个函数，你需要先在顶部或另一个模块中定义它。

此外，名称可以很长且具有描述性，这可以防止使用单独的注释。因此，代码可以更具可读性。

```
// bad
function foo() { ... }

// bad
const foo = function () { ... };

// good
// lexical name distinguished from the variable-referenced invocation(s)
const short = function longUniqueMoreDescriptiveLexicalFoo() { ... };
```

**6、在回调中优先使用箭头函数**

有些方法如 map 或 filter 将匿名函数作为参数。在这些情况下，你有很多选择，但使用箭头函数是最方便和优雅的方式。

因为，它在 this 的上下文中创建了箭头函数的一个版本，这通常是你想要的，并且是一种更简洁的语法。

```

// bad
[1, 2, 3].forEach(function (x) {
  const y = x ** 2;
  return x + y;
});

// good
[1, 2, 3].forEach((x) => {
  const y = x ** 2;
  return x + y;
});
```

**7、使用严格等于进行相等比较**

有两种类型的相等运算符：松散运算符和严格运算符。松散的是 == 和 != ，它们在没有关心类型的情况下进行比较。例如，根据松散比较，2 和 '2' 是相等的。但是，如果你使用严格的 === 和 !==，那么它也会考虑类型，这通常是预期的结果。

```
// bad
console.log(2 == '2') // true

// good
console.log(2 === '2') // false
```

**8、不要嵌套三元组**

三元运算符允许您创建内联条件语句。在 if-else 语句上使用它，你确实可以节省许多代码行。

但是，正如定义的那样，它必须是内联的和简短的。因为嵌套三元组会严重损害代码的可读性。

```

// bad
const foo = maybe1 > maybe2
  ? "bar"
  : value1 > value2 
  ? "baz" 
  : null;

// split into 2 separated ternary expressions
const maybeNull = value1 > value2 ? 'baz' : null;

// good
const foo = maybe1 > maybe2 ? 'bar' : maybeNull;
```

**9、以空格开始评论**

为了提高可读性，请确保在注释的开头放置一个空格。

```

// bad
//is current tab
let isActive = true;

// good
// is current tab
let isActive = true;
```

**10、选择正确的套管样式**

正如我在介绍中提到的，如果代码一致，大小写样式是使代码看起来不错的最重要的概念之一。在 JavaScript 中，有一些大小写样式的约定。

命名对象、函数、变量和实例时使用驼峰命名法。

仅在命名构造函数或类时使用 PascalCase。

在命名不可重新分配的变量和枚举时使用 UPPERCASE_VARIABLES。

根本不要使用 snake_case 或 kebab-case。

```

// bad
const StudentCount = 15;
class particle { ... }
function get_name() { ... }
let apiKey = 'cX25zanxsPcdjsbxX985ddXM3';

// good
const studentCount = 15;
class Particle { ... }   
function getName() { ... }
const API_KEY = 'cX25zanxsPcdjsbxX985ddXM3';
```

编写计算机可以理解的代码一点也不难。然而，编写人类容易理解的代码是一项具有挑战性的工作。这就是为什么有一些关于编码的基本规则，真的会造成好代码和坏代码之间的区别。

在本文中，我尝试使用 AirBNB 的 JavaScript 样式指南，分享我在编写好的 JavaScript 代码时不可或缺的规则。这些是我的首选，但如果你看看这个综合的风格指南，我相信你会发现一些你还不知道的东西。