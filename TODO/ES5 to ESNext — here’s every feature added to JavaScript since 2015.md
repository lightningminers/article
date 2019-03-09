---
type: FrontEnd
title: ES5 to ESNext — here’s every feature added to JavaScript since 2015
link: https://medium.freecodecamp.org/es5-to-esnext-heres-every-feature-added-to-javascript-since-2015-d0c255e13c6e
author: [Flavio Copes](https://medium.freecodecamp.org/@flaviocopes)
---
# ES5 to ESNext —  自 2015 以来 JavaScript 新增的所有新特性

![img](https://cdn-images-1.medium.com/max/2000/1*QZppItKE3Sqdi3kZA-TNGQ.png)

这篇文章的出发点是为了帮助前端开发者串联 ES6前后的 JavaScript 只是，并且可以快速了解 JavaScript 语言的最新进展。

JavaScript 在当下处于特权地位，因为它是唯一可以在浏览器中运行的语言，并且是被高度集成和优化过的。

JavaScript 在未来有着极好的发展空间，跟上它的变化不会比现在更加的困难。我的目标是让你能够快速且全面的了解这门语言可以使用的新内容。

[**点击这里获取 PDF/ePub/Mobi 版本**](https://flaviocopes.com/es5-to-next/)

#### 目录

[**ECMAScript 简介**](https://medium.com/p/d0c255e13c6e#3641)

**ES2015**

- [let 和 const](#let和const)
- [箭头函数](https://medium.com/p/d0c255e13c6e#1d7c)
- [类](https://medium.com/p/d0c255e13c6e#5609)
- [默认参数](https://medium.com/p/d0c255e13c6e#679e)
- [模板字符串](https://medium.com/p/d0c255e13c6e#1676)
- [结构赋值](https://medium.com/p/d0c255e13c6e#c962)
- [增强的对象字面量](https://medium.com/p/d0c255e13c6e#438e)
- [For-of 循环](https://medium.com/p/d0c255e13c6e#3189)
- [Promises](https://medium.com/p/d0c255e13c6e#6295)
- [模块](https://medium.com/p/d0c255e13c6e#1250)
- [String 的新方法](https://medium.com/p/d0c255e13c6e#b1bc)
- [Object 的新方法](https://medium.com/p/d0c255e13c6e#928f)
- [展开运算符](https://medium.com/p/d0c255e13c6e#c80e)
- [Set](https://medium.com/p/d0c255e13c6e#62ad)
- [Map](https://medium.com/p/d0c255e13c6e#c981)
- [Generators](https://medium.com/p/d0c255e13c6e#c668)

**ES2016**

- [Array.prototype.includes()](https://medium.com/p/d0c255e13c6e#b599)
- [求幂运算符](https://medium.com/p/d0c255e13c6e#2050)

**ES2017**

- [String 填充 padding](https://medium.com/p/d0c255e13c6e#95af)
- [Object.values()](https://medium.com/p/d0c255e13c6e#21cc)
- [Object.entries()](https://medium.com/p/d0c255e13c6e#b188)
- [Object.getOwnPropertyDescriptors()](https://medium.com/p/d0c255e13c6e#4d8c)
- [尾后逗号](https://medium.com/p/d0c255e13c6e#9e68)
- [共享内存 and 原子操作](https://medium.com/p/d0c255e13c6e#6bc5)

**ES2018**

- [Rest/Spread Properties](https://medium.com/p/d0c255e13c6e#63f6)
- [Asynchronous iteration](https://medium.com/p/d0c255e13c6e#301d)
- [Promise.prototype.finally()](https://medium.com/p/d0c255e13c6e#d396)
- [正则表达式改进](https://medium.com/p/d0c255e13c6e#3fa1)

[**ESNext**](https://medium.com/p/d0c255e13c6e#241b)

- [Array.prototype.{flat,flatMap}](https://medium.com/p/d0c255e13c6e#24dc)
- [try/catch 可选的参数绑定](https://medium.com/p/d0c255e13c6e#7b25)
- [Object.fromEntries()](https://medium.com/p/d0c255e13c6e#8aed)
- [String.prototype.{trimStart,trimEnd}](https://medium.com/p/d0c255e13c6e#ae63)
- [Symbol.prototype.description](https://medium.com/p/d0c255e13c6e#4954)
- [JSON improvements](https://medium.com/p/d0c255e13c6e#b93d)
- [Well-formed JSON.stringify()](https://medium.com/p/d0c255e13c6e#835a)
- [Function.prototype.toString()](https://medium.com/p/d0c255e13c6e#b38b)

### ECMAScript 简介

每当阅读 JavaScript 相关的文章时，我都会经常遇到如下术语： ES3, ES5, ES6, ES7, ES8, ES2015, ES2016, ES2017, ECMAScript 2017, ECMAScript 2016, ECMAScript 2015 等等，那么它们是指代的是什么？

它们指代的都是一个名为 ECMAScript 的标准。

JavaScript 就是基于这个标准实现的，ECMAScript 经常缩写为 ES。

除了 JavaScript 以外，其它基于 ECMAScript 实现语言包括：

- *ActionScript* ( Flash 脚本语言)，由于 Adobe 将于 2020 年末停止对 Flash 的支持而逐渐失去热度。
- *JScript* (微软开发的脚本语言),在第一次浏览器大战最激烈的时期，JavaScript 只被Netscape所支持，微软必须为 Internet Explorer 构建自己的脚本语言。

但是现在**流传最广**、影响最大的基于 ES 标准的语言实现无疑就是 JavaScript了

ECMAScript 这个奇怪的名称起源是什么呢？**Ecma International** 是瑞士标准协会，负责制定国际标准。

JavaScript 被创建以后，经由 Netscape 和 Sun Microsystems 公司提交给欧洲计算机制造商协会进行标准化，被采纳的 ECMA-262 又被称为  **ECMAScript**。

[This press release by Netscape and Sun Microsystems](https://web.archive.org/web/20070916144913/http://wp.netscape.com/newsref/pr/newsrelease67.html) (the maker of Java) might help figure out the name choice, which might include legal and branding issues by Microsoft which was in the committee, [according to Wikipedia](https://en.wikipedia.org/wiki/ECMAScript).

在 IE9 之后，在微软的浏览器中就看不到对 JScript 这个命名的引用，取而代之的是统称为 JavaScript。

因此，截至201x，JavaScript 成为最流行的基于 ECMAScript 规范实现的语言。

#### ECMAScript 当前的版本。

目前的最新的 ECMAScript 版本是 **ES2018**。

于 2018 年 6 月发布。

#### TC39 是什么？

TC39（Technical Committee 39）是一个推动 JavaScript 发展的委员会。

C39的成员是 它的成员包括各个主流浏览器厂商以及业务与浏览器紧密相连的公司，其中包括 Mozilla，Google ，Facebook，Apple，Microsoft，Intel，PayPal，SalesForce等。

每个标准版本提案都必须经过四个不同的阶段，[这里有详细的解释](https://tc39.github.io/process-document/)。

#### ES Versions

令我费解的是 ES 版本的命名依据有时根据迭代的版本号，有时却根据年份来进行命名。而这个命名的不确定性又使得人们更加容易混淆 JS/ES 这个两个概念😄。

在 ES2015 之前，ECMAScript 各个版本的命名规范通常与跟着标准的版本更新保持一致。因此，2009年 ECMAScript 规范更新以后的的正式版本是 ES5。

Why does this happen? During the process that led to ES2015, the name was changed from ES6 to ES2015, but since this was done late, people still referenced it as ES6, and the community has not left the edition naming behind — *the world is still calling ES releases by edition number*.

This table should clear things up a bit:



![img](https://cdn-images-1.medium.com/max/1600/1*ta8eBjBIGeJucahugjlopg.png)

接下啦我们来深入了解 JavaScript 自 ES5 以来增加的特性。

### let和const

ES2015 之前, `var` 是唯一可以用来声明变量的语句。

```js
var a = 0
```

上面语句如果你遗漏了 `var`，那么你会把这个值（0）赋给一个未声明的变量，其中声明和未声明变量之间存在一些差异。

在现代浏览器开启严格模式时，给未声明的变量赋值会抛出 ReferenceError 异常，在较老的浏览器（或者禁用严格模式）的情况下，未声明的变量在执行赋值操作时会隐式的变为全局对象的属性。

当你声明一个变量却没有进行初始化，那么它的值直到你对它进行赋值操作之前都是 `undefined` 。

```js
var a //typeof a === 'undefined'
```

你可以对一个变量进行多次变量，后面声明语句会覆盖之前的：

```js
var a = 1
var a = 2
```

你也可以在一条声明语句中一次声明多个变量：

```js
var a = 1, b = 2
```

**作用域**是可访问变量的集合。

在函数外部用声明 `var` 声明的变量会成为全局变量的属性，这种变量可以在全局作用域中被访问到。而在函数内部声明的变量只能在函数局部作用域被访问到，在这点上类似于函数参数。

在函数中定义的局部变量名如何跟全局变量重名，那么局部变量的优先级更高，在函数内无法访问到同名的全局变量。

需要注意的是，`var` 是没有块级作用域（标识符是一对花括号）的，但是 `var` 是有函数作用域的，所以在新创建的块级作用域或者是函数作用域里面声明变量会覆盖全局同名变量，因为 `var` 在这两种情况下没有创建新的作用域。

在函数内部，其中定义的任何变量在所有函数代码中都是可见的，因为JavaScript在执行代码之前实际上将所有变量都移到了顶层（被称为悬挂的东西）。
在函数的内部定义的变量在整个函数作用域中都是可见（可访问），即使变量是在函数体末尾被声明，但是仍然可以再函数体开头部分被引用，因为 JavaScript存在**变量提升**机制。为避免混淆，请在函数开头声明变量，养成良好的编码规范。

#### Using `let`

`let` 是ES2015中引入的新功能，它本质上是具有块级作用域的 `var` 。它可以被当前作用域（函数以及块级作用域）以及子级作用域访问到。

现代 JavaScript 开发者在 `let` 和 `var` 的选择中可能会更倾向于前者。

> **如果** `*let*` **看起来比较抽象，那么试着读一下这段代码** `*let color = 'red'*`就好像是 让颜色变为红色，这样可能会更加有感性的认识（译者：这段我真的不会翻译了）。

Defining `let` outside of any function - contrary to `var` - does not create a global variable.

#### Using `const`

使用变量 `var` 或 `let` 声明的变量可以被重新赋值。 使用 `const` 声明的变量一经初始化，它的值就永远不能再改变，即不可重新被赋值。

```js
const a = 'test'
```

我们不能再为 `a` 进行赋值操作。然而，`a` 如果它是一个具有属性或者方法的对象，那么我们可以改变它的属性或者方法。

`const` 并不意味着具有不可变性，只是保证用 `const` 声明的变量的引用地址不被变更。

类似于 `let`，`const` 也具有块级作用域。

现代 JavaScript 开发者在遇到不会进行二次赋值的变量声明时，应该尽量使用 `const`。

### 箭头函数

箭头函数的引入极大的改变了代码的书写风格和一些工作机制。

在我看来，箭头函数很受开发者欢迎，现在很少在比较新的代码库中看到 `function` 关键字了，虽然它并未被废弃。

箭头函数看起来会更加的简洁，因为它允许您你使用更短的语法来书写函数：

```js
const myFunction = function() {
  //...
}
```

到

```js
const myFunction = () => {
  //...
}
```

如果函数体重只包含一条语句，你甚至可以省略括号并直接书写这条语句：

```js
const myFunction = () => doSomething()
```

参数在括号中传递：

```js
const myFunction = (param1, param2) => doSomething(param1, param2)
```

如果该函数**只有一个**参数，那么可以省略掉括号：

```js
const myFunction = param => doSomething(param)
```

Thanks to this short syntax, arrow functions **encourage the use of small functions**.
由于这种简短的语法，使得我们可以更便捷的使用**比较简短的函数**

#### 隐式返回

箭头函数支持隐式返回：可以正常的 `return` 一个返回值但是可以不使用 `return` 关键字。

隐式返回只在函数体内只包含一条语句的情况下生效：

```js
const myFunction = () => 'test'
myFunction() //'test'
```

需要注意的一种情况，当返回一个对象时，记得将大括号括在括号中以避免产生歧义，误将其（大括号）解析为函数体的大括号。

```js
const myFunction = () => ({ value: 'test' })
myFunction() //{value: 'test'}
```

#### 箭头函数中的 `this`

`this` 可能是一个很难掌握的概念，因为它会根据上下文而进行变化，并且会在不同的 JavaScript的模式（是否为*严格模式*）下表现存在差异。

理解 `this` 这个概念对于箭头函数的使用很重要，因为与常规函数相比，箭头函数的表现非常不同。

对象的方法为常规函数时，方法中的`this`指向这个对象，因此可以这样做：

```js
const car = {
  model: 'Fiesta',
  manufacturer: 'Ford',
  fullName: function() {
    return `${this.manufacturer} ${this.model}`
  }
}
```

执行 `car.fullName()` 会返回 `"Ford Fiesta"`。

如果上述方法使用是是箭头函数，由于箭头中的 `this` 的作用域继承自执行上下文，箭头函数自身不绑定 `this`，因此 `this` 的值将在调用堆栈中查找，因此在此代码 `car.fullName()` 中不会返回常规函数那样的结果，实际会返回字符串 "undefined undefined"：

```js
const car = {
  model: 'Fiesta',
  manufacturer: 'Ford',
  fullName: () => {
    return `${this.manufacturer} ${this.model}`
  }
}
```

因此，箭头函数不适合作为对象方法。

同样，箭头函数也不适合使用在作为创建构造函数,因为在实例化对象时会抛出 `TypeError`。

所以在**不需要动态上下文时**请使用常规函数。

当然，在事件监听器上使用箭头函数也会存在问题。因为 DOM 事件侦听器会自动将 `this` 与目标元素绑定，如果该事件处理程序的逻辑依赖 `this`，那么需要常规函数：

```js
const link = document.querySelector('#link')
link.addEventListener('click', () => {
  // this === window
})
const link = document.querySelector('#link')
link.addEventListener('click', function() {
  // this === link
})
```

### Classes

JavaScript 实现继承的方式比较罕见：[原型继承]((https://flaviocopes.com/javascript-prototypal-inheritance/))。原型继承虽然在我看来很棒，但与其他大多数流行的编程语言的继承实现机制不同，后者是基于类的。

因此 Java、Python 或其他语言的开发者很难理解原型继承的方式，因此 ECMAScript 委员会决定在原型继承之上实现 class 的语法糖，这样便于就跟其他基于类的继承语言的开发者更好的理解 JavaScript 代码。

This is important: JavaScript under the hood is still the same, and you can access an object prototype in the usual way.

注意：class 并没有对 JavaScript 底层做修改，你仍然可以直接访问对象原型。
#### class 定义

如下是一个 class  的例子：

```js
class Person {
  constructor(name) {
    this.name = name
  }
  hello() {
    return 'Hello, I am ' + this.name + '.'
  }
}
```

 class 具有一个标识符，我们可以使用 `new ClassIdentifier()` 来创建一个对象实例。

初始化对象时，调用 `constructor`方法，并将参数传递给此方法。

类声明语句中也可以增加类需要的一些原型方法。在这种情况下 `hello` 是 `Person` 类的一个原型方法，可以在这个类的对象实例上调用：

```js
const flavio = new Person('Flavio')
flavio.hello()
```

#### Class 继承

一个类还可以通过 `extends` 创建子类，通过子类实例化出来的队形可以继承这两个类的所有方法。

如果子类中的方法与父类中的方法名重复，那么子类中的同名方法优先级更高：

```js
class Programmer extends Person {
  hello() {
    return super.hello() + ' I am a programmer.'
  }
}
const flavio = new Programmer('Flavio')
flavio.hello()
```

(上述代码会打印出：“*Hello, I am Flavio. I am a programmer.*”)

Classes do not have explicit class variable declarations, but you must initialize any variable in the constructor.

在子类中，你可以通过调用`super()`引用父类。

#### 静态方法

在类中，通常会把方法直接挂载到实例对象上，直接在实例对象上可以调用。

而实例方法则是直接使用类名来调用，而不是通过对象实例调用：

```js
class Person {
  static genericHello() {
    return 'Hello'
  }
}
Person.genericHello() //Hello
```

#### 私有方法

JavaScript 没有内置真正意义上的受保护的私有方法。

社区有解决方法，但我不会在这里做讲解。

#### Getters 和 setters

你可以通过增加方法 前缀 `get` 或者 `set` 创建一个 getter 和 setter, getter 和 setter会在你去获取特定值或者修改特定值的时候执行 `get` 或者 `set`内的相关方法。

```js
class Person {
  constructor(name) {
    this._name = name
  }
  set name(value) {
    this._name = value
  }
  get name() {
    return this._name
  }
}
```

如果您只有一个 getter，则无法设置该属性，并且设置此属性的操作都会被忽略：

```js
class Person {
  constructor(name) {
    this._name = name
  }
  get name() {
    return this._name
  }
}
```

如果您只有一个 setter，则无法设置该属性，并且设置此属性的操作都会被忽略：

```js
class Person {
  constructor(name) {
    this._name = name
  }
  set name(value) {
    this._name = value
  }
}
```

### 默认参数

函数 `doSomething`  接收一个 `param1` 参数。

```js
const doSomething = (param1) => {
}
```

我们可以给 *param1* 设定默认值，如果在调用函数时未传入参数，那么该参数自动设定未默认值。

```js
const doSomething = (param1 = 'test') => {
}
```

当然，这中机制同样适用于多个参数：

```js
const doSomething = (param1 = 'test', param2 = 'test2') => {
}
```

假如你的函数是一个具有特定属性的对象改怎么处理？

曾几何时，如果我们必须需要取一个对象的特定属性值，为了做兼容处理（对象格式不正确），你必须在函数中添加一些代码：

```js
const colorize = (options) => {
  if (!options) {
    options = {}
  }
  const color = ('color' in options) ? options.color : 'yellow'
  ...
}
```

通过解构，你可以给队形的特定属性提供默认值，而这样则可以大大简化代码。

```js
const colorize = ({ color = 'yellow' }) => {
  ...
}
```

如果在调用 `colorize` 函数时没有传递任何对象，我们同样可以得到一个默认对象作为参数以供使用：

```js
const spin = ({ color = 'yellow' } = {}) => {
  ...
}
```

### 模板字符串

模板字符串不同于 ES5 以前的版本，你可以用新颖的方式使用字符串。

这个语法看起来非常简便，只需要使用一个反引号替换掉单引号或双引号：

```js
const a_string = `something`
```

这个用法是第一无二的，因为它提供了许多普通字符串所没有的功能，如下：

- 它为定义多行字符串提供了一个很好的语法
- 它提供了一种在字符串中插入变量和表达式的简单方法
- 它允许您创建带有模板标签的DSL ( DSL意味着特定于域的语言，例如，它在“由样式化组件反应”中用于定义组件的CSS )

下面让我们深入每个功能的细节。

#### 多行字符串

在 ES6 标准之前，创建跨越两行的字符串只能在一行的结尾使用 '\' 字符：

```js
const string =
  'first part \
second part'
```

这样使得你创建的字符串虽然跨越了两汉，但是渲染时仍然表现成一行：

```js
first part second part
```

需要渲染为多行的话，需要在一行结尾添加 '\n'，比如这样：

```js
const string =
  'first line\n \
second line'
```

或者

```js
const string = 'first line\n' + 'second line'
```

模板字符串使得定义多行字符串变得更加简便。

一个模板字符串由一个反引号开始，你只需要按下回车键来创建新的一行，不需要插入特殊符号，最终的渲染效果如下所示：

```js
const string = `Hey
this
string
is awesome!`
```

需要特别留意空格在这里是有特殊意义的，如果这样做的话：

```js
const string = `First
                Second`
```

那么它会创建出像下面的字符串：

```js
First
                Second
```

有一个简单的方法可以修复这个问题，只需要将第一行置为空，然后添加了右边的翻译好后调用一个 trim() 方法，就可以消除第一个字符前的所有空格：
```js
const string = `
First
Second`.trim()
```

#### 插值

模板字符串提供了插入变量和表达式的便捷方法

你只需要使用 ${...} 语法

```js
const var = 'test'
const string = `something ${var}` //something test
```

在 ${} 里面你可以加入任何东西，甚至是表达式：

```js
const string = `something ${1 + 2 + 3}`
const string2 = `something ${foo() ? 'x' : 'y'}`
```

#### Template tags

标记模板可能是一个听起来不太有用的功能，但它实际上被许多流行的库使用，如 Styled Components 、Apollo 、GraphQL客户端/服务器库，因此了解它的工作原理至关重要。

在 Styled Components 模板标签中用于定义CSS字符串

```js
const Button = styled.button`
  font-size: 1.5em;
  background-color: black;
  color: white;
`
```

在 Apollo 中，模板标签用于定义 GraphQL 查询模式：

```js
const query = gql`
  query {
    ...
  }
`
```

上面两个例子中的`styled.button`和`gql`模板标签其实都是**函数**:

```
function gql(literals, ...expressions) {}
```

这个函数返回一个字符串，可以是*任意*类型的计算结果。

`字面量`(literals)是一个包含了表达式插值的模板字面量的序列。
`表达式`(expressions)包含了所有的插值。

举个例子：

```
const string = `something ${1 + 2 + 3}`
```

这个例子里面的`字面量`是一个由2个部分组成的序列。第1部分就是`something`，也就是第一个插值位置(${})之前的字符串，第2部分就是一个空字符串，从第1个插值结束的位置直到字符串的结束。

这个例子里面的`表达式`就是只包含1个部分的序列，也就是`6`。

举一个更复杂的例子：

```
const string = `something
another ${'x'}
new line ${1 + 2 + 3}
test`
```

这个例子里面的`字面量`的序列里面，第1个部分是：

```
;`something
another `
```

第2部分是：

```
;`
new line `
```

第3部分是：

```
;`
test`
```

这个例子里面的`表达式`包含了2个部分：`x`和`6`。

拿到了这些值的函数就可以对其做任意处理，这就是这个特性的威力所在。

比如最简单的处理就是字符串插值，把`字面量`和`表达式`拼接起来：

```
const interpolated = interpolate`I paid ${10}€`
```

`插值`的过程就是：

```
function interpolate(literals, ...expressions) {
  let string = ``
  for (const [i, val] of expressions) {
    string += literals[i] + val
  }
  string += literals[literals.length - 1]
  return string
}
```

### 解构赋值

给定一个object，你可以抽取其中的一些值并且赋值给命名的变量：

```
const person = {
  firstName: 'Tom',
  lastName: 'Cruise',
  actor: true,
  age: 54, //made up
}
const {firstName: name, age} = person
```

`name`和`age`就包含了对应的值。

这个语法同样可以用到数组当中：

```
const a = [1,2,3,4,5]
const [first, second] = a
```

下面这个语句创建了3个新的变量，分别取的是数组`a`的第0、1、4下标对应的值：

```
const [first, second, , , fifth] = a
```

### 更强大的对象字面量

ES2015赋予了对象字面量更大的威力。

#### 简化了包含变量的语法

原来的写法：

```
const something = 'y'
const x = {
  something: something
}
```

新的写法：

```
const something = 'y'
const x = {
  something
}
```

#### 原型

原型可以这样指定：

```
const anObject = { y: 'y' }
const x = {
  __proto__: anObject
}
```

#### super()

```
const anObject = { y: 'y', test: () => 'zoo' }
const x = {
  __proto__: anObject,
  test() {
    return super.test() + 'x'
  }
}
x.test() //zoox
```

#### 动态属性

```
const x = {
  ['a' + '_' + 'b']: 'z'
}
x.a_b //z
```

### For-of循环

2009年的ES5引入了`forEach()`循环。虽然很好用，但是它跟`for`循环一样，没法break。

ES2015引入了`**for-of**` **循环**, 就是在`forEach`的基础上加上了break的功能：

```
//iterate over the value
for (const v of ['a', 'b', 'c']) {
  console.log(v);
}
//get the index as well, using `entries()`
for (const [i, v] of ['a', 'b', 'c'].entries()) {
  console.log(index) //index
  console.log(value) //value
}
```

留意一下`const`的使用。这个循环在每次迭代中都会创建一个新的作用域，所以我们可以使用`const`来代替`let`。

它跟`for...in`的区别在于：

- `for...of` **遍历属性值**
- `for...in` **遍历属性名**

### Promises

promise的一般定义： **它是一个代理，通过它可以最终得到一个值**.

Promise是处理异步代码的一种方式，可以少写很多回调。

**异步函数**是建立在promise API上面的，所以理解Promise是一个基本的要求。

#### promise的原理简述

一个promise被调用的时候，首先它是处于**pending**状态。在promise处理的过程中，调用的函数（caller）可以继续执行，直到promise给出反馈。

此时，调用的函数等待的promise结果要么是**resolved**状态，要么是**rejected**状态。但是由于[JavaScript](https://flaviocopes.com/javascript/)是异步的，所以*promise处理的过程中，函数会继续执行*。

#### 为什么JS API使用promises?

除了你的代码和第三方库的代码之外，promise在用在现代的Web API中，比如：

- 电池API
- [Fetch API](https://flaviocopes.com/fetch-api/)
- [Service Workers](https://flaviocopes.com/service-workers/)

在现代的JavaScript中，不使用promise是太可能的，所以我们来深入研究下promise吧。

#### 创建一个promise

Promise API暴露了一个Promise构造函数，可以通过`new Promise()`来初始化：

```
let done = true
const isItDoneYet = new Promise((resolve, reject) => {
  if (done) {
    const workDone = 'Here is the thing I built'
    resolve(workDone)
  } else {
    const why = 'Still working on something else'
    reject(why)
  }
})
```

promise会检查`done`这个全局变量，如果为true，就返回一个resolved promise，否则就返回一个rejected promise。

通过`resolve`和`reject`，我们可以得到一个返回值，返回值可以是字符串也可以是对象。

#### 使用一个promise

上面讲了怎么创建一个promise，下面就讲怎么使用（consume）这个promise。

```
const isItDoneYet = new Promise()
//...
const checkIfItsDone = () => {
  isItDoneYet
    .then(ok => {
      console.log(ok)
    })
    .catch(err => {
      console.error(err)
    })
}
```

运行`checkIfItsDone()`方法时，会执行`isItDoneYet()`这个promise，并且等待它resolve的时候使用`then`回调，如果有错误，就用`catch`回调来处理。

#### 链式promise

一个promise可以返回另一个promise，从而创建promise链接（chain）。

一个很好的例子就是[Fetch API](https://flaviocopes.com/fetch-api)，它是基于XMLHttpRequest API的一个上层API，我们可以用它来获取资源，并且在获取到资源的时候链式执行一系列promise。

Fetch API是一个基于promise的机制，调用`fetch()`相当于使用`new Promise()`来声明我们自己的promise。

#### 链式promise的例子

```
const status = response => {
  if (response.status >= 200 && response.status < 300) {
    return Promise.resolve(response)
  }
  return Promise.reject(new Error(response.statusText))
}
const json = response => response.json()
fetch('/todos.json')
  .then(status)
  .then(json)
  .then(data => {
    console.log('Request succeeded with JSON response', data)
  })
  .catch(error => {
    console.log('Request failed', error)
  })
```

在这个例子当中，我们调用`fetch()`，从根目录的`todos.json`文件中获取一系列的TODO项目，并且创建一个链式promise。

运行`fetch()`方法会返回一个[response](https://fetch.spec.whatwg.org/#concept-response)，它包含很多属性，我们从中引用如下属性：

- `status`, 一个数值，表示HTTP状态码
- `statusText`, 一个状态消息，当请求成功的时候返回`OK`

`response`还有一个`json()`方法，它返回一个promise，返回内容转换成JSON后的结果。

所以这些promise的调用过程就是：第一个promise执行一个我们定义的`status()`方法，检查response status，判断是否一个成功的响应(status在200和299之间)，如果不是成功的响应，就reject这个promise。

这个reject操作会导致整个链式promise跳过后面的所有promise直接到`catch()`语句，打印`Request failed`和错误消息。

如果这个promise成功了，它会调用我们定义的json()函数。因为前面的promise成功之后返回的`response`对象，我们可以拿到并作为第2个promise的参数传入。

在这个例子里面，我们返回了JSON序列化的数据，所以第3个promise直接接收这个JSON：

```
.then((data) => {
  console.log('Request succeeded with JSON response', data)
})
```

然后我们把它打印到console。

#### 处理错误

在上一节的的例子里面，我们有一个`catch`接在链式promise后面。

当promise链中的任意一个出错或者reject的时候，就会直接跳到promise链后面最近的`catch()`语句。

```
new Promise((resolve, reject) => {
  throw new Error('Error')
}).catch(err => {
  console.error(err)
})
// or
new Promise((resolve, reject) => {
  reject('Error')
}).catch(err => {
  console.error(err)
})
```

#### 级联错误

如果在`catch()`里面抛出一个错误，你可以在后面接上第二个`catch()`来处理这个错误，以此类推。

```
new Promise((resolve, reject) => {
  throw new Error('Error')
})
  .catch(err => {
    throw new Error('Error')
  })
  .catch(err => {
    console.error(err)
  })
```

#### 组织多个promise

#### `Promise.all()`

如果你要同时完成不同的promise,可以用`Promise.all()`来声明一系列的promise，然后当它们全部resolve的时候再执行一些操作。

例子：

```
const f1 = fetch('/something.json')
const f2 = fetch('/something2.json')
Promise.all([f1, f2])
  .then(res => {
    console.log('Array of results', res)
  })
  .catch(err => {
    console.error(err)
  })
```

结合ES2015的解构赋值语法，你可以这样写：

```
Promise.all([f1, f2]).then(([res1, res2]) => {
  console.log('Results', res1, res2)
})
```

当然这不限于使用`fetch`， **这适用于任何promise**.

#### `Promise.race()`

`Promise.race()`运行所有传递进去的promise，但是只要有其中一个resolve了，就会运行后面的回调，并且只执行一次回调，回调的参数就是第一个resolve的promise返回的结果。

例子：

```
const promiseOne = new Promise((resolve, reject) => {
  setTimeout(resolve, 500, 'one')
})
const promiseTwo = new Promise((resolve, reject) => {
  setTimeout(resolve, 100, 'two')
})
Promise.race([promiseOne, promiseTwo]).then(result => {
  console.log(result) // 'two'
})
```

### 模块

ES Module是一个关于多模块的ECMAScript标准。

Node.js用了CommonJS标准好几年了，但是浏览器从来没有一个模块系统，, the browser never had a module system, as every major decision such as a module system must be first standardized by ECMAScript and then implemented by the browser.

This standardization process completed with ES2015 and browsers started implementing this standard trying to keep everything well aligned, working all in the same way, and now ES Modules are supported in Chrome, Safari, Edge and Firefox (since version 60).

模块非常酷，他们可以让你封装各种各样的功能，同时将这些功能作为库暴露给其他 JavaScript 文件使用。

#### ES 模块语法

引入模块的语法:

```
import package from 'module-name'
```

CommonJS 则是这样使用：

```
const package = require('module-name')
```

一个模块是一个 JavaScript 文件，这个文件使用 `export` 关键字 **exports** 一个或多个值（对象、函数或者变量）。例如，下面这个模块提供了一个将字符串变成大写形式的函数：

> *uppercase.js*

```
export default str => str.toUpperCase()
```

在这个例子中，这个模块定义了唯一一个 **default export**，因此可以是一个匿名函数。否则，需要一个名称来和其他 **exports** 做区分。

现在，**任何其他的 JavaScript 模块** 可以通过 **import** 导入 **uppercase.js** 的这个功能。

一个 HTML 页面可以通过使用了特殊的 `type=module` 属性的 `<script>` 标签添加一个模块。

```
<script type="module" src="index.js"></script>
```

> *注意: 这个模块导入的行为就像 `*defer*` 脚本加载一样。具体可以看* [*efficiently load JavaScript with defer and async*](https://flaviocopes.com/javascript-async-defer/)

需要特别注意的是，任何通过 `type="module"` 载入的脚本会使用 *strict mode* 加载。

在这个例子中，`uppercase.js` 模块定义了一个 **default export**，因此当我们在导入它的时候，我们可以给他起一个任何我们喜欢的名字：

```
import toUpperCase from './uppercase.js'
```

同时我们可以这样使用它:

```
toUpperCase('test') //'TEST'
```

你也可以通过一个绝对路径来导入模块，下面是一个引用来自其他域底下定义的模块的例子：

```
import toUpperCase from 'https://flavio-es-modules-example.glitch.me/uppercase.js'
```

下面同样是一些合法的 *import*语法：

```
import { toUpperCase } from '/uppercase.js'
import { toUpperCase } from '../uppercase.js'
```

下面是错误的使用:

```
import { toUpperCase } from 'uppercase.js'
import { toUpperCase } from 'utils/uppercase.js'
```

因为这里既不是使用绝对地址，也不是使用的相对地址。

#### 其它的 import/export 语法

我们了解了上面的例子： 

```
export default str => str.toUpperCase()
```

这里生成了一个 *default export*。然而，你可以通过下面的语法在一个文件里面 *export* 多个功能：

```
const a = 1
const b = 2
const c = 3
export { a, b, c }
```
另外一个模块可以使用下面的方式 *import* 所有这些 *exports*：

```
import * from 'module'
```

你也可以通过解构赋值的方式仅仅 *import* 一部分 *exports*：

```
import { a } from 'module'
import { a, b } from 'module'
```

为了方便，你还可以使用 `as` 重命名任何 *import* 的东西：

```
import { a, b as two } from 'module'
```

你可以导入模块中的默认出口以及通过名称导入任何非默认的出口：

```
import React, { Component } from 'react'
```

这是一篇关于 ES 模块的文章，可以看一下： <https://glitch.com/edit/#!/flavio-es-modules-example?path=index.html>

#### CORS(跨域资源共享)

进行远程获取模块的时候是遵循 CORS 机制的。这意味着当你引用远程模块的时候，必须使用合法的 CORS 请求头来允许跨域访问（例如：`Access-Control-Allow-Origin: *`）。

#### 对于不支持模块的浏览器应该怎么做？

结合 `type="module"`、`nomodule` 一起使用：

```
<script type="module" src="module.js"></script>
<script nomodule src="fallback.js"></script>
```

#### 包装模块

ES 模块是现代浏览器中的一大特性。这些特性是 ES6 规范中的一部分，要在浏览器中全部实现这些特性的路还很漫长。

我们现在就能使用它们！但是我们同样需要知道，有一些模块会对我们的页面性能产生性能影响。因为浏览器必须要在运行时执行它们。

Webpack 可能仍然会被大量使用，即使 ES 模块可以在浏览器中执行。但是语言内置这个特性对于客户端和 nodejs 在使用模块的时候是一种巨大的统一。

### 新的字符串方法

任何字符串有了一些实例方法：

- `repeat()`
- `codePointAt()`

#### repeat()

根据指定的次数重复字符串：

```
'Ho'.repeat(3) //'HoHoHo'
```

没有提供参数以及使用 `0` 作为参数的时候返回空字符串。如果给一个负数参数则会得到一个 `RangeError` 的错误。

#### codePointAt()

这个方法能用在处理那些需要 2 个 UTF-16 单元表示的字符上。

使用 `charCodeAt` 的话，你需要先分别得到两个 UTF-16 的编码然后结合它们。但是使用 `codePointAt()` 你可以直接得到整个字符。

下面是一个例子，中文的 “𠮷” 是由两个 UTF-16 编码组合而成的：

```
"𠮷".charCodeAt(0).toString(16) //d842
"𠮷".charCodeAt(1).toString(16) //dfb7
```

如果你将两个 unicode 字符组合起来：

```
"\ud842\udfb7" //"𠮷"
```

你也可以用 `codePointAt()` 得到同样的结果:

```
"𠮷".codePointAt(0) //20bb7
```

如果你将得到的 unicode 编码组合起来：

```
"\u{20bb7}" //"𠮷"
```

更多关于 Unicode 的使用方法，参考我的[Unicode guide](https://flaviocopes.com/unicode/)。

### 新的对象方法

ES2015 在 Object 类下引入了一些静态方法：

- `Object.is()` 确定两个值是不是同一个
- `Object.assign()` 用来浅拷贝一个对象
- `Object.setPrototypeOf` 设置一个对象的原型

#### Object.is()

这个方法用来帮助比较对象的值：

使用方式:

```
Object.is(a, b)
```

返回值在下列情况之外一直是 `false`：

- `a` 和 `b` 是同一个对象
- `a` 和 `b` 是相等的字符串(用同样的字符组合在一起的字符串是相等的)
- `a` 和 `b` 是相等的数字
- `a` 和 `b` 都是 `undefined`, `null`, `NaN`, `true` 或者都是 `false`

`0` 和 `-0` 在 JavaScript 里面是不同的值, 所以对这种情况要多加小心（例如在比较之前，使用 `+` 一元操作符将所有值转换成 `+0`）。

#### Object.assign()

在 `ES2015` 版本中引入，这个方法拷贝所有给出的对象中的可枚举的自身属性到另一个对象中。

这个 API 的基本用法是创建一个对象的浅拷贝。

```
const copied = Object.assign({}, original)
```

作为浅拷贝，值会被复制，对象则是拷贝其引用（不是对象本身），因此当你修改了源对象的一个属性值，这个修改也会在拷贝出的对象中生效，因为内部引用的对象是相同的。:

```
const original = {
  name: 'Fiesta',
  car: {
    color: 'blue'
  }
}
const copied = Object.assign({}, original)
original.name = 'Focus'
original.car.color = 'yellow'
copied.name //Fiesta
copied.car.color //yellow
```

我之前提到过，源对象可以是`一个或者多个`:

```
const wisePerson = {
  isWise: true
}
const foolishPerson = {
  isFoolish: true
}
const wiseAndFoolishPerson = Object.assign({}, wisePerson, foolishPerson)
console.log(wiseAndFoolishPerson) //{ isWise: true, isFoolish: true }
```

#### Object.setPrototypeOf()

设置一个对象的原型。可以接受两个参数：对象以及原型。

使用方法:

```
Object.setPrototypeOf(object, prototype)
```

例子:

```
const animal = {
  isAnimal: true
}
const mammal = {
  isMammal: true
}
mammal.__proto__ = animal
mammal.isAnimal //true
const dog = Object.create(animal)
dog.isAnimal  //true
console.log(dog.isMammal)  //undefined
Object.setPrototypeOf(dog, mammal)
dog.isAnimal //true
dog.isMammal //true
```

### 展开操作符

你可以展开一个数组、一个对象甚至是一个字符串，通过使用展开操作符 `...`。

让我们以数组来举例，给出：

```
const a = [1, 2, 3]
```

你可以使用下面的方式创建出一个新的数组：

```
const b = [...a, 4, 5, 6]
```

你也可以像下面这样创建一个数组的拷贝：

```
const c = [...a]
```

这中方式对于对象仍然有效。使用下面的方式克隆一个对象：

```
const newObj = { ...oldObj }
```

用在字符串上的时候，展开操作符会以字符串中的每一个字符创建一个数组：

```
const hey = 'hey'
const arrayized = [...hey] // ['h', 'e', 'y']
```

这个操作符有一些非常有用的应用。其中最重要的一点就是以一种非常简单的方式使用数组作为函数参数的能力：

```
const f = (foo, bar) => {}
const a = [1, 2]
f(...a)
```

（在之前的语法规范中，你只能通过 `f.apply(null, a)` 的方式来实现，但是这种方式不是很友好和易读。）

剩余参数（**rest element**）在和数组解构（**array destructuring**）搭配使用的时候非常有用。

```
const numbers = [1, 2, 3, 4, 5]
[first, second, ...others] = numbers
```

下面是展开元素 （**spread elements**）:

```
const numbers = [1, 2, 3, 4, 5]
const sum = (a, b, c, d, e) => a + b + c + d + e
const sum = sum(...numbers)
```

ES2018 引入了 **剩余属性** ，同样的操作符但是只能用在对象上。

剩余属性（**Rest properties**）:

```
const { first, second, ...others } = {
  first: 1,
  second: 2,
  third: 3,
  fourth: 4,
  fifth: 5
}
first // 1
second // 2
others // { third: 3, fourth: 4, fifth: 5 }
```

属性展开（**Spread properties**）允许我们结合跟在 `...` 操作符之后对象的属性：

```
const items = { first, second, ...others }
items //{ first: 1, second: 2, third: 3, fourth: 4, fifth: 5 }
```

### Set

一个 Set 数据结构允许我们在一个容器里面增加数据。

一个 Set 是一个对象或者基础数据类型（strings、numbers或者booleans）的集合，你可以将它看作是一个 Map，其中值作为映射键，map 值始终为 true。

#### 初始化一个 Set

Set 可以通过下面的方式初始化：

```
const s = new Set()
```

#### 向 Set 中添加一项

你可以使用 `add` 方法向 Set 中添加项：

```
s.add('one')
s.add('two')
```
Set 仅会存贮唯一的元素，因此多次调用 `s.add('one')` 不会重复添加新的元素。

你不可以同时向 set 中加入多个元素。你需要多次调用 `add()` 方法。

#### 检查元素是否在 set 中

我们可以通过下面的方式检查元素是否在 set 中：

```
s.has('one') //true
s.has('three') //false
```

#### 从 set 中删除一个元素：

使用 `delete()` 方法：

```
s.delete('one')
```

#### 确定 set 中元素的数量

使用 `size` 属性：

```
s.size
```

#### 删除 set 中的全部元素

使用 `clear()` 方法：

```
s.clear()
```

#### 对 set 进行迭代

使用 `keys()` 或者 `values()` 方法 - 它们等价于下面的代码：

```
for (const k of s.keys()) {
  console.log(k)
}
for (const k of s.values()) {
  console.log(k)
}
```

`entries()` 方法返回一个迭代器，你可以这样使用它：

```
const i = s.entries()
console.log(i.next())
```

调用 `i.next()` 将会以 `{ value, done = false }` 对象的形式返回每一个元素，直到迭代结束，这时 `done` 是 `true`。

你也可以调用 set 的 `forEach()` 方法：

```
s.forEach(v => console.log(v))
```

或者你就直接使用 `for..of` 循环吧：

```
for (const k of s) {
  console.log(k)
}
```

#### 使用一些初始值初始化一个 set

你可以使用一些值初始化一个 set：

```
const s = new Set([1, 2, 3, 4])
```

#### 将 set 转换位一个数组

```
const a = [...s.keys()]
// or
const a = [...s.values()]
```

#### WeakSet

一个 WeakSet 是一个特殊的 Set.

在 set 中，元素不会被 gc（垃圾回收）。一个 weakSet 让它的所有元素都是可以被 gc 的。weakSet 中的每个键都是一个对象。当这个对象的引用消失的时候，对应的值就可以被 gc 了。

下面是主要的不同点：

1. WeakSet 不可迭代
2. 你不能清空 weakSet 中的所有元素
3. 不能够得到 weakSet 的大小

一个 weakSet 通常是在框架级别的代码中使用，仅仅暴露了下面的方法：

- add()
- has()
- delete()

### Map

Map 数据结构就是一个键值对。

#### Before ES6

Before its introduction, people generally used objects as maps, by associating some object or value to a specific key value:

```
const car = {}
car['color'] = 'red'
car.owner = 'Flavio'
console.log(car['color']) //red
console.log(car.color) //red
console.log(car.owner) //Flavio
console.log(car['owner']) //Flavio
```

#### Enter Map

ES6 introduced the Map data structure, providing us a proper tool to handle this kind of data organization.

A Map is initialized by calling:

```
const m = new Map()
```

#### Add items to a Map

You can add items to the map by using the `set` method:

```
m.set('color', 'red')
m.set('age', 2)
```

#### Get an item from a map by key

And you can get items out of a map by using `get`:

```
const color = m.get('color')
const age = m.get('age')
```

#### Delete an item from a map by key

Use the `delete()` method:

```
m.delete('color')
```

#### Delete all items from a map

Use the `clear()` method:

```
m.clear()
```

#### Check if a map contains an item by key

Use the `has()` method:

```
const hasColor = m.has('color')
```

#### Find the number of items in a map

Use the `size` property:

```
const size = m.size
```

#### Initialize a map with values

You can initialize a map with a set of values:

```
const m = new Map([['color', 'red'], ['owner', 'Flavio'], ['age', 2]])
```

#### Map keys

Just like any value (object, array, string, number) can be used as the value of the key-value entry of a map item, **any value can be used as the key**, even objects.

If you try to get a non-existing key using `get()` out of a map, it will return `undefined`.

#### Weird situations you’ll almost never find in real life

```
const m = new Map()
m.set(NaN, 'test')
m.get(NaN) //test
const m = new Map()
m.set(+0, 'test')
m.get(-0) //test
```

#### Iterate over map keys

Map offers the `keys()` method we can use to iterate on all the keys:

```
for (const k of m.keys()) {
  console.log(k)
}
```

#### Iterate over map values

The Map object offers the `values()` method we can use to iterate on all the values:

```
for (const v of m.values()) {
  console.log(v)
}
```

#### Iterate over map key, value pairs

The Map object offers the `entries()` method we can use to iterate on all the values:

```
for (const [k, v] of m.entries()) {
  console.log(k, v)
}
```

which can be simplified to

```
for (const [k, v] of m) {
  console.log(k, v)
}
```

#### Convert the map keys into an array

```
const a = [...m.keys()]
```

#### Convert the map values into an array

```
const a = [...m.values()]
```

#### WeakMap

A WeakMap is a special kind of map.

In a map object, items are never garbage collected. A WeakMap instead lets all its items be freely garbage collected. Every key of a WeakMap is an object. When the reference to this object is lost, the value can be garbage collected.

Here are the main differences:

1. you cannot iterate over the keys or values (or key-values) of a WeakMap
2. you cannot clear all items from a WeakMap
3. you cannot check its size

A WeakMap exposes those methods, which are equivalent to the Map ones:

- `get(k)`
- `set(k, v)`
- `has(k)`
- `delete(k)`

The use cases of a WeakMap are less evident than the ones of a Map, and you might never find the need for them, but essentially it can be used to build a memory-sensitive cache that is not going to interfere with garbage collection, or for careful encapsulation and information hiding.

### Generators

Generators are a special kind of function with the ability to pause itself, and resume later, allowing other code to run in the meantime.

See the full JavaScript Generators Guide for a detailed explanation of the topic.

The code decides that it has to wait, so it lets other code “in the queue” to run, and keeps the right to resume its operations “when the thing it’s waiting for” is done.

All this is done with a single, simple keyword: `yield`. When a generator contains that keyword, the execution is halted.

A generator can contain many `yield` keywords, thus halting itself multiple times, and it's identified by the `*function` keyword, which is not to be confused with the pointer dereference operator used in lower level programming languages such as C, C++ or Go.

Generators enable whole new paradigms of programming in JavaScript, allowing:

- 2-way communication while a generator is running
- long-lived while loops which do not freeze your program

Here is an example of a generator which explains how it all works.

```
function *calculator(input) {
    var doubleThat = 2 * (yield (input / 2))
    var another = yield (doubleThat)
    return (input * doubleThat * another)
}
```

We initialize it with

```
const calc = calculator(10)
```

Then we start the iterator on our generator:

```
calc.next()
```

This first iteration starts the iterator. The code returns this object:

```
{
  done: false
  value: 5
}
```

What happens is: the code runs the function, with `input = 10` as it was passed in the generator constructor. It runs until it reaches the `yield`, and returns the content of `yield`: `input / 2 = 5`. So we got a value of 5, and the indication that the iteration is not done (the function is just paused).

In the second iteration we pass the value `7`:

```
calc.next(7)
```

and what we got back is:

```
{
  done: false
  value: 14
}
```

`7` was placed as the value of `doubleThat`. Important: you might read like `input / 2` was the argument, but that's just the return value of the first iteration. We now skip that, and use the new input value, `7`, and multiply it by 2.

We then reach the second yield, and that returns `doubleThat`, so the returned value is `14`.

In the next, and last, iteration, we pass in 100

```
calc.next(100)
```

and in return we got

```
{
  done: true
  value: 14000
}
```

As the iteration is done (no more yield keywords found) and we just return `(input * doubleThat * another)` which amounts to `10 * 14 * 100`.

------

Those were the features introduced in ES2015. Let’s now dive into ES2016 which is much smaller in scope.

------

### Array.prototype.includes()

This feature introduces a more readable syntax for checking if an array contains an element.

With ES6 and lower, to check if an array contained an element you had to use `indexOf`, which checks the index in the array, and returns `-1` if the element is not there.

Since `-1` is evaluated as a true value, you could **not** do for example

```
if (![1,2].indexOf(3)) {
  console.log('Not found')
}
```

With this feature introduced in ES7 we can do

```
if (![1,2].includes(3)) {
  console.log('Not found')
}
```

### Exponentiation Operator

The exponentiation operator `**` is the equivalent of `Math.pow()`, but brought into the language instead of being a library function.

```
Math.pow(4, 2) == 4 ** 2
```

This feature is a nice addition for math intensive JS applications.

The `**` operator is standardized across many languages including Python, Ruby, MATLAB, Lua, Perl and many others.



![img](https://cdn-images-1.medium.com/max/1600/1*ta8eBjBIGeJucahugjlopg.png)

------

Those were the features introduced in 2016. Let’s now dive into 2017

------

### String padding

The purpose of string padding is to **add characters to a string**, so it **reaches a specific length**.

ES2017 introduces two `String` methods: `padStart()` and `padEnd()`.

```
padStart(targetLength [, padString])
padEnd(targetLength [, padString])
```

Sample usage:



![img](https://cdn-images-1.medium.com/max/1600/1*dn9xi0ABHBNXUClPtUMPEg.png)

### Object.values()

This method returns an array containing all the object own property values.

Usage:

```
const person = { name: 'Fred', age: 87 }
Object.values(person) // ['Fred', 87]
```

`Object.values()` also works with arrays:

```
const people = ['Fred', 'Tony']
Object.values(people) // ['Fred', 'Tony']
```

### Object.entries()

This method returns an array containing all the object own properties, as an array of `[key, value]` pairs.

Usage:

```
const person = { name: 'Fred', age: 87 }
Object.entries(person) // [['name', 'Fred'], ['age', 87]]
```

`Object.entries()` also works with arrays:

```
const people = ['Fred', 'Tony']
Object.entries(people) // [['0', 'Fred'], ['1', 'Tony']]
```

### Object.getOwnPropertyDescriptors()

This method returns all own (non-inherited) properties descriptors of an object.

Any object in JavaScript has a set of properties, and each of these properties has a descriptor.

A descriptor is a set of attributes of a property, and it’s composed by a subset of the following:

- **value**: the value of the property
- **writable**: true the property can be changed
- **get**: a getter function for the property, called when the property is read
- **set**: a setter function for the property, called when the property is set to a value
- **configurable**: if false, the property cannot be removed nor any attribute can be changed, except its value
- **enumerable**: true if the property is enumerable

`Object.getOwnPropertyDescriptors(obj)` accepts an object, and returns an object with the set of descriptors.

#### In what way is this useful?

ES6 gave us `Object.assign()`, which copies all enumerable own properties from one or more objects, and return a new object.

However there is a problem with that, because it does not correctly copies properties with non-default attributes.

If an object for example has just a setter, it’s not correctly copied to a new object, using `Object.assign()`.

For example with

```
const person1 = {
    set name(newName) {
        console.log(newName)
    }
}
```

This won’t work:

```
const person2 = {}
Object.assign(person2, person1)
```

But this will work:

```
const person3 = {}
Object.defineProperties(person3,
  Object.getOwnPropertyDescriptors(person1))
```

As you can see with a simple console test:

```
person1.name = 'x'
"x"
person2.name = 'x'
person3.name = 'x'
"x"
```

`person2` misses the setter, it was not copied over.

The same limitation goes for shallow cloning objects with **Object.create()**.

### Trailing commas

This feature allows to have trailing commas in function declarations, and in functions calls:

```
const doSomething = (var1, var2,) => {
  //...
}
doSomething('test2', 'test2',)
```

This change will encourage developers to stop the ugly “comma at the start of the line” habit.

### Async functions

JavaScript evolved in a very short time from callbacks to promises (ES2015), and since ES2017 asynchronous JavaScript is even simpler with the async/await syntax.

Async functions are a combination of promises and generators, and basically, they are a higher level abstraction over promises. Let me repeat: **async/await is built on promises**.

#### Why were async/await introduced?

They reduce the boilerplate around promises, and the “don’t break the chain” limitation of chaining promises.

When Promises were introduced in ES2015, they were meant to solve a problem with asynchronous code, and they did, but over the 2 years that separated ES2015 and ES2017, it was clear that *promises could not be the final solution*.

Promises were introduced to solve the famous *callback hell* problem, but they introduced complexity on their own, and syntax complexity.

They were good primitives around which a better syntax could be exposed to developers, so when the time was right we got **async functions**.

They make the code look like it’s synchronous, but it’s asynchronous and non-blocking behind the scenes.

#### How it works

An async function returns a promise, like in this example:

```
const doSomethingAsync = () => {
  return new Promise(resolve => {
    setTimeout(() => resolve('I did something'), 3000)
  })
}
```

When you want to **call** this function you prepend `await`, and **the calling code will stop until the promise is resolved or rejected**. One caveat: the client function must be defined as `async`. Here's an example:

```
const doSomething = async () => {
  console.log(await doSomethingAsync())
}
```

#### A quick example

This is a simple example of async/await used to run a function asynchronously:

```
const doSomethingAsync = () => {
  return new Promise(resolve => {
    setTimeout(() => resolve('I did something'), 3000)
  })
}
const doSomething = async () => {
  console.log(await doSomethingAsync())
}
console.log('Before')
doSomething()
console.log('After')
```

The above code will print the following to the browser console:

```
Before
After
I did something //after 3s
```

#### 关于 Promise

将 `async` 关键字标记在任何函数上，意味着这个函数都将返回一个 Promise，即使这个函数没有显式的返回，它在内部也会返回一个 Promise，这就是下面这份代码有效的原因：

``` javascript
const aFunction = async () => {
  return 'test'
}
aFunction().then(alert) // This will alert 'test'
```

下面的例子也一样:

```javascript
const aFunction = async () => {
  return Promise.resolve('test')
}
aFunction().then(alert) // This will alert 'test'
```

#### 更易于阅读的代码

正如上述的例子，我们将它与普通回调函数或链式函数进行比较，我们的代码看起来非常的简单。

这是一个很简单的例子，当代码足够复杂时，它会产生更多的收益。

例如，使用 Promise 来获取 JSON 资源并解析它：

```javascript
const getFirstUserData = () => {
  return fetch('/users.json') // get users list
    .then(response => response.json()) // parse JSON
    .then(users => users[0]) // pick first user
    .then(user => fetch(`/users/${user.name}`)) // get user data
    .then(userResponse => response.json()) // parse JSON
}
getFirstUserData()
```

这是使用 async/await 实现相同功能的例子：

```javascript
const getFirstUserData = async () => {
  const response = await fetch('/users.json') // get users list
  const users = await response.json() // parse JSON
  const user = users[0] // pick first user
  const userResponse = await fetch(`/users/${user.name}`) // get user data
  const userData = await user.json() // parse JSON
  return userData
}
getFirstUserData()
```

#### 串行多个异步功能

async 函数非常容易，并且它的语法比 Promise 更易读。


```javascript
const promiseToDoSomething = () => {
  return new Promise(resolve => {
    setTimeout(() => resolve('I did something'), 10000)
  })
}
const watchOverSomeoneDoingSomething = async () => {
  const something = await promiseToDoSomething()
  return something + ' and I watched'
}
const watchOverSomeoneWatchingSomeoneDoingSomething = async () => {
  const something = await watchOverSomeoneDoingSomething()
  return something + ' and I watched as well'
}
watchOverSomeoneWatchingSomeoneDoingSomething().then(res => {
  console.log(res)
})
```

打印结果:

```
I did something and I watched and I watched as well
```

#### 更简单的调试

调试 Promise 就很困难，因为调试器无法跨越异步代码，但调试 async/await 就非常的简单，调试器会像调试同步代码一样来处理它。

### 共享内存和原子

WebWorkers 可以在浏览器中创建多线程程序。

它们通过事件的方式来传递消息，从 ES2017 开始，你可以使用 `SharedArrayBuffer` 在每一个 Worker 中和它们的创建者之间共享内存数组.

由于不知道写入内存部分需要多长的周期来广播，因此在读取值时，任何类型的写入操作都会完成，`Atomics` 可以避免 竞争条件的发生。
Since it’s unknown how much time writing to a shared memory portion takes to propagate, **Atomics** are a way to enforce that when reading a value, any kind of writing operation is completed.

关于它的更多细节可以在[proposal](https://github.com/tc39/ecmascript_sharedmem/blob/master/TUTORIAL.md)中找到。

------

这是 ES2017，接下来我将介绍 ES2018 的功能。

------

### Rest/Spread Properties

ES2015 引入了解构数组的方法，当你使用时：

```javascript
const numbers = [1, 2, 3, 4, 5]
[first, second, ...others] = numbers
```

and **展开参数**:

```javascript
const numbers = [1, 2, 3, 4, 5]
const sum = (a, b, c, d, e) => a + b + c + d + e
const sum = sum(...numbers)
```

ES2018 为对象引入了同样的功能。

**解构**:

```javascript
const { first, second, ...others } = { first: 1, second: 2, third: 3, fourth: 4, fifth: 5 }
first // 1
second // 2
others // { third: 3, fourth: 4, fifth: 5 }
```

**展开熟悉** 允许通过组合在展开运算符之后传递的对象属性而创建新对象：

```javascript
const items = { first, second, ...others }
items //{ first: 1, second: 2, third: 3, fourth: 4, fifth: 5 }
```

### 异步迭代器

The new construct `for-await-of` allows you to use an async iterable object as the loop iteration:

`for-await-of` 允许你使用异步可迭代对象做为循环迭代：


```javascript
for await (const line of readLines(filePath)) {
  console.log(line)
}
```

因为它使用的了 `await`，因此你只能在 `async` 函数中使用它。

### Promise.prototype.finally()

当一个 Promise 是 fulfilled 时，它会一个接一个的调用 then。

如果在这个过程中发生了错误，则会跳过 `then` 而执行 `catch`。

而 `finally()` 允许你运行一些代码，无论是成功还是失败：

```javascript
fetch('file.json')
  .then(data => data.json())
  .catch(error => console.error(error))
  .finally(() => console.log('finished'))
```

### 正则表达式改进

ES2018 对正则表达式引入了许多改进，这些都可以在 <https://flaviocopes.com/javascript-regular-expressions/> 上找到。

以下是关于 ES2018 正则表达式改进的具体补充：

#### RegExp lookbehind assertions: 根据前面的内容匹配字符串

这是一个 lookahead: 你可以使用 `?=` 来匹配字符串，后面跟随一个特定的字符串：

```javascript
/Roger(?=Waters)/
/Roger(?= Waters)/.test('Roger is my dog') //false
/Roger(?= Waters)/.test('Roger is my dog and Roger Waters is a famous musician') //true
```

`?!` 可以执行逆操作，如果匹配的字符串是**no**而不是在此后跟随特定的子字符串的话：

```javascript
/Roger(?!Waters)/
/Roger(?! Waters)/.test('Roger is my dog') //true
/Roger(?! Waters)/.test('Roger Waters is a famous musician') //false
```


Lookaheads 使用 `?=` Symbol，它们已经可以用了。

**Lookbehinds**, 是一个新功能使用`?<=`.

```javascript
/(?<=Roger) Waters/
/(?<=Roger) Waters/.test('Pink Waters is my dog') //false
/(?<=Roger) Waters/.test('Roger is my dog and Roger Waters is a famous musician') //true
```

如果一个 lookbehind 是否定，那么使用 `?>!`:

```javascript
/(?<!Roger) Waters/
/(?<!Roger) Waters/.test('Pink Waters is my dog') //true
/(?<!Roger) Waters/.test('Roger is my dog and Roger Waters is a famous musician') //false
```

#### Unicode属性转义 `\p{…}` and `\P{…}`

在正则表达式模式中，你可以使用 `\d` 来匹配任意的数字，`\s` 来匹配任意不是空格的字符串，`\w` 来匹配任意字母数字字符串，以此类推。

This new feature extends this concept to all Unicode characters introducing `\p{}` and is negation `\P{}`.

Any unicode character has a set of properties. For example `Script`determines the language family, `ASCII` is a boolean that's true for ASCII characters, and so on. You can put this property in the graph parentheses, and the regex will check for that to be true:

```
/^\p{ASCII}+$/u.test('abc')   //✅
/^\p{ASCII}+$/u.test('ABC@')  //✅
/^\p{ASCII}+$/u.test('ABC🙃') //❌
```

`ASCII_Hex_Digit` is another boolean property, that checks if the string only contains valid hexadecimal digits:

```
/^\p{ASCII_Hex_Digit}+$/u.test('0123456789ABCDEF') //✅
/^\p{ASCII_Hex_Digit}+$/u.test('h')                //❌
```

There are many other boolean properties, which you just check by adding their name in the graph parentheses, including `Uppercase`, `Lowercase`, `White_Space`, `Alphabetic`, `Emoji` and more:

```
/^\p{Lowercase}$/u.test('h') //✅
/^\p{Uppercase}$/u.test('H') //✅
/^\p{Emoji}+$/u.test('H')   //❌
/^\p{Emoji}+$/u.test('🙃🙃') //✅
```

In addition to those binary properties, you can check any of the unicode character properties to match a specific value. In this example, I check if the string is written in the greek or latin alphabet:

```
/^\p{Script=Greek}+$/u.test('ελληνικά') //✅
/^\p{Script=Latin}+$/u.test('hey') //✅
```

Read more about all the properties you can use [directly on the proposal](https://github.com/tc39/proposal-regexp-unicode-property-escapes).

#### Named capturing groups

In ES2018 a capturing group can be assigned to a name, rather than just being assigned a slot in the result array:

```
const re = /(?<year>\d{4})-(?<month>\d{2})-(?<day>\d{2})/
const result = re.exec('2015-01-02')
// result.groups.year === '2015';
// result.groups.month === '01';
// result.groups.day === '02';
```

#### The `s` flag for regular expressions

The `s` flag, short for *single line*, causes the `.` to match new line characters as well. Without it, the dot matches regular characters but not the new line:

```
/hi.welcome/.test('hi\nwelcome') // false
/hi.welcome/s.test('hi\nwelcome') // true
```

------

### ESNext

What’s next? ESNext.

ESNext is a name that always indicates the next version of JavaScript.

The current ECMAScript version is **ES2018**. It was released in June 2018.

Historically JavaScript editions have been standardized during the summer, so we can expect **ECMAScript 2019** to be released in summer 2019.

So at the time of writing, ES2018 has been released, and **ESNext is ES2019**

Proposals to the ECMAScript standard are organized in stages. Stages 1–3 are an incubator of new features, and features reaching Stage 4 are finalized as part of the new standard.

At the time of writing we have a number of features at **Stage 4**. I will introduce them in this section. The latest versions of the major browsers should already implement most of those.

Some of those changes are mostly for internal use, but it’s also good to know what is going on.

There are other features at Stage 3, which might be promoted to Stage 4 in the next few months, and you can check them out on this GitHub repository: <https://github.com/tc39/proposals>.

### Array.prototype.{flat,flatMap}

`flat()` is a new array instance method that can create a one-dimensional array from a multidimensional array.

Example:

```
['Dog', ['Sheep', 'Wolf']].flat()
//[ 'Dog', 'Sheep', 'Wolf' ]
```

By default it only “flats” up to one level, but you can add a parameter to set the number of levels you want to flat the array to. Set it to `Infinity` to have unlimited levels:

```
['Dog', ['Sheep', ['Wolf']]].flat()
//[ 'Dog', 'Sheep', [ 'Wolf' ] ]
['Dog', ['Sheep', ['Wolf']]].flat(2)
//[ 'Dog', 'Sheep', 'Wolf' ]
['Dog', ['Sheep', ['Wolf']]].flat(Infinity)
//[ 'Dog', 'Sheep', 'Wolf' ]
```

If you are familiar with the JavaScript `map()` method of an array, you know that using it you can execute a function on every element of an array.

`flatMap()` is a new Array instance method that combines `flat()` with `map()`. It's useful when calling a function that returns an array in the map() callback, but you want your resulted array to be flat:

```
['My dog', 'is awesome'].map(words => words.split(' '))
//[ [ 'My', 'dog' ], [ 'is', 'awesome' ] ]
['My dog', 'is awesome'].flatMap(words => words.split(' '))
//[ 'My', 'dog', 'is', 'awesome' ]
```

### Optional catch binding

Sometimes we don’t need to have a parameter bound to the catch block of a try/catch.

We previously had to do:

```js
try {
  //...
} catch (e) {
  //handle error
}
```

Even if we never had to use `e` to analyze the error. We can now simply omit it:

```
try {
  //...
} catch {
  //handle error
}
```

### Object.fromEntries()

Objects have an `entries()` method, since ES2017.

It returns an array containing all the object own properties, as an array of `[key, value]` pairs:

```
const person = { name: 'Fred', age: 87 }
Object.entries(person) // [['name', 'Fred'], ['age', 87]]
```

ES2019 introduces a new `Object.fromEntries()` method, which can create a new object from such array of properties:

```
const person = { name: 'Fred', age: 87 }
const entries = Object.entries(person)
const newPerson = Object.fromEntries(entries)

person !== newPerson //true 
```

### String.prototype.{trimStart,trimEnd}

This feature has been part of v8/Chrome for almost a year now, and it’s going to be standardized in ES2019.

#### `trimStart()`

Return a new string with removed white space from the start of the original string

```
'Testing'.trimStart() //'Testing'
' Testing'.trimStart() //'Testing'
' Testing '.trimStart() //'Testing '
'Testing'.trimStart() //'Testing'
```

#### `trimEnd()`

Return a new string with removed white space from the end of the original string

```
'Testing'.trimEnd() //'Testing'
' Testing'.trimEnd() //' Testing'
' Testing '.trimEnd() //' Testing'
'Testing '.trimEnd() //'Testing'
```

### Symbol.prototype.description

You can now retrieve the description of a symbol by accessing its `description`property instead of having to use the `toString()` method:

```
const testSymbol = Symbol('Test')
testSymbol.description // 'Test'
```

### JSON improvements

Before this change, the line separator (\u2028) and paragraph separator (\u2029) symbols were not allowed in strings parsed as JSON.

Using JSON.parse(), those characters resulted in a `SyntaxError` but now they parse correctly, as defined by the JSON standard.

### Well-formed JSON.stringify()

Fixes the `JSON.stringify()` output when it processes surrogate UTF-8 code points (U+D800 to U+DFFF).

Before this change calling `JSON.stringify()` would return a malformed Unicode character (a "�").

Now those surrogate code points can be safely represented as strings using `JSON.stringify()`, and transformed back into their original representation using `JSON.parse()`.

### Function.prototype.toString()

Functions have always had an instance method called `toString()` which return a string containing the function code.

ES2019 introduced a change to the return value to avoid stripping comments and other characters like whitespace, exactly representing the function as it was defined.

If previously we had

```
function /* this is bar */ bar () {}
```

The behavior was this:

```
bar.toString() //'function bar() {}
```

now the new behavior is:

```
bar.toString(); // 'function /* this is bar */ bar () {}'
```

------

Wrapping up, I hope this article helped you catch up on some of the latest JavaScript additions, and the new features we’ll see in 2019.

[**Click here to get a PDF / ePub / Mobi version of this post to read offline**](https://flaviocopes.com/es5-to-next/)