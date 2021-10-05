# JavaScript命名约定规则整理

来源 | https://www.robinwieruch.de/javascript-naming-conventions

今天跟大家分享的是JavaScript 命名约定示例介绍——它为你提供了在 JavaScript 中命名变量、函数、类或组件时的常识。没有人强制执行这些命名约定规则，但是，它们在JavaScript开发中被广泛接受为标准。

## **01、变量**

JavaScript 变量区分大小写。因此，带有小写和大写字符的 JavaScript 变量是不同的：

```
var name = 'Robin Wieruch';

var Name = 'Dennis Wieruch';

var NAME = 'Thomas Wieruch';

console.log(name);
// "Robin Wieruch"

console.log(Name);
// "Dennis Wieruch"

console.log(NAME);
// "Thomas Wieruch"
```

一个JavaScript变量应该是自我描述。不需要为变量添加附加文档的注释：

```

// bad
var value = 'Robin';

// bad
var val = 'Robin';

// good
var firstName = 'Robin';
```

大多数情况下，你会发现使用带有前导小写字符的驼峰式变量名声明的 JavaScript 变量：

 

```
// bad
var firstname = 'Robin';

// bad
var first_name = 'Robin';

// bad
var FIRSTNAME = 'Robin';

// bad
var FIRST_NAME = 'Robin';

// good
var firstName = 'Robin';
```

JavaScript 常量、私有和类/组件有例外——我们将在后面探讨。然而，一般来说，JavaScript 变量——一个字符串、布尔值或数字，以及一个对象、数组或函数——是用驼峰式变量名声明的。

关于不同案例样式的简要概述：

- camelCase（在 JS 中使用）
- PascalCase（在 JS 中使用）
- snake_case
- kebab-case

**02、布尔值**

像 is、are 或 has 这样的前缀可以帮助每个 JavaScript 开发人员通过查看布尔值和其他变量来区分它：

```
// bad
var visible = true;

// good
var isVisible = true;

// bad
var equal = false;

// good
var areEqual = false;

// bad
var encryption = true;

// good
var hasEncryption = true;
```

与字符串和整数相比，你可以将其视为 JavaScript 布尔命名约定的另一个软规则，除了以驼峰命名。

**03、函数**
JavaScript 函数也是用驼峰式编写的。此外，最佳实践是通过给函数名称一个动词作为前缀来实际告诉函数正在做什么。

```
// bad
function name(firstName, lastName) {
  return `${firstName} ${lastName}`;
}

// good
function getName(firstName, lastName) {
  return `${firstName} ${lastName}`;
}
```

这个动词作为前缀可以是任何东西（例如get、fetch、push、apply、calculate、compute、post）。对于拥有更多自我描述性 JavaScript 变量，这是另一个需要考虑的软规则。

## **04、类**

与其他 JavaScript 数据结构相比，JavaScript 类使用 PascalCase 声明：

```
class SoftwareDeveloper {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }
}

var me = new SoftwareDeveloper('Robin', 'Wieruch');
```

每次调用 JavaScript 构造函数来实例化一个类的新实例时，类的名称都应该出现在 Pascal Case 中，因为该类首先是用 Pascal Case 声明的。

## **05、组件**

组件在 JavaScript 中并非无处不在，但在React等前端框架中很常见。由于组件有点实例化——而是附加到 DOM 中——就像一个 JavaScript 类，它们也被广泛地用 Pascal Case 声明。

```
// bad
function userProfile(user) {
  return (
    <div>
      <span>First Name: {user.firstName}</span>
      <span>Last Name: {user.lastName}</span>
    </div>
  );
}

// good
function UserProfile(user) {
  return (
    <div>
      <span>First Name: {user.firstName}</span>
      <span>Last Name: {user.lastName}</span>
    </div>
  );
}
```

当一个组件被使用时，它区别于原生 HTML 和web 组件，因为它的第一个字母总是大写的。

```
<div>
  <UserProfile
    user={{ firstName: 'Robin', lastName: 'Wieruch' }}
  />
</div>
```

## **06、方法**

与 JavaScript 函数相同，JavaScript 类上的方法使用驼峰命名法声明：

```
class SoftwareDeveloper {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }

  getName() {
    return `${this.firstName} ${this.lastName}`;
  }
}

var me = new SoftwareDeveloper('Robin', 'Wieruch');

console.log(me.getName());
// "Robin Wieruch"
```

此处适用与 JavaScript 函数相同的规则——例如添加动词作为前缀——以使方法名称更具自我描述性。

## **07、私有**

在 JavaScript 中，你很少会在变量/函数/方法前面找到下划线 ( _ )。如果你看到一个，它旨在为私人。尽管 JavaScript 不能真正强制执行它，但将某些内容声明为 private 告诉我们应该如何使用它或不应该如何使用它。

例如，类中的私有方法只能在类内部使用，而应避免在类的实例上使用：

```
class SoftwareDeveloper {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.name = _getName(firstName, lastName);
  }

  _getName(firstName, lastName) {
    return `${firstName} ${lastName}`;
  }
}

var me = new SoftwareDeveloper('Robin', 'Wieruch');

// good
var name = me.name;
console.log(name);
// "Robin Wieruch"

// bad
name = me._getName(me.firstName, me.lastName);
console.log(name);
// "Robin Wieruch"
```

私有变量/函数也可以出现在 JavaScript 文件中。这可能意味着变量/函数不应该在这个文件之外使用，而只能在内部为同一文件中的其他函数计算进一步的业务逻辑。

## **08、常量**

最后，但并非最不重要的是，在 JavaScript 中有一些常量——旨在成为不变的变量——用大写字母（大写）写成：

```
var SECONDS = 60;
var MINUTES = 60;
var HOURS = 24;

var DAY = SECONDS * MINUTES * HOURS;
```

如果一个变量的变量声明名称中包含多个单词，则使用下划线 ( _ )：

```
var DAYS_UNTIL_TOMORROW = 1 ;
```

通常 JavaScript 常量定义在 JavaScript 文件的顶部。正如之前所暗示的，除了原始数据结构的变量的const 声明之外，没有人强制一个人不要改变这里的变量，但它的大写命名建议避免它。

## **09、全局变量**

JavaScript 变量是全局定义的，如果它的所有上下文都可以访问它。上下文通常由声明/定义变量的 JavaScript 文件定义，但在较小的 JavaScript 项目中，它可能是整个项目。全局 JavaScript 变量没有特殊的命名约定。

- 全局 JavaScript 变量在项目/文件的顶部声明。
- 如果全局 JavaScript 变量是可变的，则它会以驼峰命名。
- 如果全局 JavaScript 变量是不可变的，则它以大写形式写入。

## **10、下划线**

那么 JavaScript 变量命名中的下划线和破折号呢？由于在 JS 中主要考虑了驼峰式大小写和 PascalCase，你已经看到下划线很少用于私有变量或常量。有时，你会在从第三方（如数据库或API）获取信息时发现下划线。你可能会看到下划线的另一种情况是未使用的函数参数，但如果你还没有在那里看到它们，请不要担心这些 ;-)

## **11、DASH**

JavaScript 变量中的破折号也不是常识。它只会让事情变得更加困难；就像在对象中使用它们一样：

```
// bad
var person = {
  'first-name': 'Robin',
  'last-name': 'Wieruch',
};

var firstName = person['first-name'];

// good
var person = {
  firstName: 'Robin',
  lastName: 'Wieruch',
};

var firstName = person.firstName;
```

甚至不可能直接对变量声明使用破折号：

```
var first-name = 'Robin';
// Uncaught SyntaxError: Unexpected token '-'
```

这就是为什么最好避免它们。

## **12、文件**

JavaScript 中有两种命名文件的策略：PascalCase 和 kebab-case。在 JavaScript 前端应用程序中，你经常会看到 PascalCase 用于命名组件（例如 React 组件）。

```
- components/
--- user/
----- UserProfile.js
----- UserList.js
----- UserItem.js
--- ui/
----- Dialog.js
----- Dropdown.js
----- Table.js
```

相比之下，在 JavaScript 后端应用程序中，kebab-case 是常识：

```
- routing/
--- user-route.js
--- messages-route.js
```

你还将看到驼峰命名法，但与 PascalCase（抱歉，前端应用程序）类似，存在操作系统以不同方式处理它们的风险，这可能会导致错误。这就是为什么坚持 kebab-case 应该成为 JavaScript 中文件名的规范。