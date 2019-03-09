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

Modules are very cool, because they let you encapsulate all sorts of functionality, and expose this functionality to other JavaScript files, as libraries.

#### The ES Modules Syntax

The syntax to import a module is:

```
import package from 'module-name'
```

while CommonJS uses

```
const package = require('module-name')
```

A module is a JavaScript file that **exports** one or more values (objects, functions or variables), using the `export` keyword. For example, this module exports a function that returns a string uppercase:

> *uppercase.js*

```
export default str => str.toUpperCase()
```

In this example, the module defines a single, **default export**, so it can be an anonymous function. Otherwise it would need a name to distinguish it from other exports.

Now, **any other JavaScript module** can import the functionality offered by uppercase.js by importing it.

An HTML page can add a module by using a `<script>` tag with the special `type="module"` attribute:

```
<script type="module" src="index.js"></script>
```

> *Note: this module import behaves like a* `*defer*` *script load. See* [*efficiently load JavaScript with defer and async*](https://flaviocopes.com/javascript-async-defer/)

It’s important to note that any script loaded with `type="module"` is loaded in strict mode.

In this example, the `uppercase.js` module defines a **default export**, so when we import it, we can assign it a name we prefer:

```
import toUpperCase from './uppercase.js'
```

and we can use it:

```
toUpperCase('test') //'TEST'
```

You can also use an absolute path for the module import, to reference modules defined on another domain:

```
import toUpperCase from 'https://flavio-es-modules-example.glitch.me/uppercase.js'
```

This is also valid import syntax:

```
import { toUpperCase } from '/uppercase.js'
import { toUpperCase } from '../uppercase.js'
```

This is not:

```
import { toUpperCase } from 'uppercase.js'
import { toUpperCase } from 'utils/uppercase.js'
```

It’s either absolute, or has a `./` or `/` before the name.

#### Other import/export options

We saw this example above:

```
export default str => str.toUpperCase()
```

This creates one default export. In a file however you can export more than one thing, by using this syntax:

```
const a = 1
const b = 2
const c = 3
export { a, b, c }
```

Another module can import all those exports using

```
import * from 'module'
```

You can import just a few of those exports, using the destructuring assignment:

```
import { a } from 'module'
import { a, b } from 'module'
```

You can rename any import, for convenience, using `as`:

```
import { a, b as two } from 'module'
```

You can import the default export, and any non-default export by name, like in this common React import:

```
import React, { Component } from 'react'
```

You can see an ES Modules example here: <https://glitch.com/edit/#!/flavio-es-modules-example?path=index.html>

#### CORS

Modules are fetched using CORS. This means that if you reference scripts from other domains, they must have a valid CORS header that allows cross-site loading (like `Access-Control-Allow-Origin: *`)

#### What about browsers that do not support modules?

Use a combination of `type="module"` and `nomodule`:

```
<script type="module" src="module.js"></script>
<script nomodule src="fallback.js"></script>
```

#### Wrapping up modules

ES Modules are one of the biggest features introduced in modern browsers. They are part of ES6 but the road to implement them has been long.

We can now use them! But we must also remember that having more than a few modules is going to have a performance hit on our pages, as it’s one more step that the browser must perform at runtime.

Webpack is probably going to still be a huge player even if ES Modules land in the browser, but having such a feature directly built in the language is huge for a unification of how modules work client-side and on Node.js as well.

### New String methods

Any string value got some new instance methods:

- `repeat()`
- `codePointAt()`

#### repeat()

Repeats the strings for the specified number of times:

```
'Ho'.repeat(3) //'HoHoHo'
```

Returns an empty string if there is no parameter, or the parameter is `0`. If the parameter is negative you'll get a RangeError.

#### codePointAt()

This method can be used to handle Unicode characters that cannot be represented by a single 16-bit Unicode unit, but need 2 instead.

Using `charCodeAt()` you need to retrieve the first, and the second, and combine them. Using `codePointAt()` you get the whole character in one call.

For example, this Chinese character “𠮷” is composed by 2 UTF-16 (Unicode) parts:

```
"𠮷".charCodeAt(0).toString(16) //d842
"𠮷".charCodeAt(1).toString(16) //dfb7
```

If you create a new character by combining those unicode characters:

```
"\ud842\udfb7" //"𠮷"
```

You can get the same result sign `codePointAt()`:

```
"𠮷".codePointAt(0) //20bb7
```

If you create a new character by combining those unicode characters:

```
"\u{20bb7}" //"𠮷"
```

More on Unicode and working with it in my [Unicode guide](https://flaviocopes.com/unicode/).

### New Object methods

ES2015 introduced several static methods under the Object namespace:

- `Object.is()` determines if two values are the same value
- `Object.assign()` used to shallow copy an object
- `Object.setPrototypeOf` sets an object prototype

#### Object.is()

This methods aims to help comparing values.

Usage:

```
Object.is(a, b)
```

The result is always `false` unless:

- `a` and `b` are the same exact object
- `a` and `b` are equal strings (strings are equal when composed by the same characters)
- `a` and `b` are equal numbers (numbers are equal when their value is equal)
- `a` and `b` are both `undefined`, both `null`, both `NaN`, both `true` or both `false`

`0` and `-0` are different values in JavaScript, so pay attention in this special case (convert all to `+0` using the `+` unary operator before comparing, for example).

#### Object.assign()

Introduced in `ES2015`, this method copies all the **enumerable own properties** of one or more objects into another.

Its primary use case is to create a shallow copy of an object.

```
const copied = Object.assign({}, original)
```

Being a shallow copy, values are cloned, and objects references are copied (not the objects themselves), so if you edit an object property in the original object, that’s modified also in the copied object, since the referenced inner object is the same:

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

I mentioned “one or more”:

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

Set the prototype of an object. Accepts two arguments: the object and the prototype.

Usage:

```
Object.setPrototypeOf(object, prototype)
```

Example:

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

### The spread operator

You can expand an array, an object or a string using the spread operator `...`

Let’s start with an array example. Given

```
const a = [1, 2, 3]
```

you can create a new array using

```
const b = [...a, 4, 5, 6]
```

You can also create a copy of an array using

```
const c = [...a]
```

This works for objects as well. Clone an object with:

```
const newObj = { ...oldObj }
```

Using strings, the spread operator creates an array with each char in the string:

```
const hey = 'hey'
const arrayized = [...hey] // ['h', 'e', 'y']
```

This operator has some pretty useful applications. The most important one is the ability to use an array as function argument in a very simple way:

```
const f = (foo, bar) => {}
const a = [1, 2]
f(...a)
```

(In the past you could do this using `f.apply(null, a)` but that's not as nice and readable.)

The **rest element** is useful when working with **array destructuring**:

```
const numbers = [1, 2, 3, 4, 5]
[first, second, ...others] = numbers
```

and **spread elements**:

```
const numbers = [1, 2, 3, 4, 5]
const sum = (a, b, c, d, e) => a + b + c + d + e
const sum = sum(...numbers)
```

ES2018 introduces rest properties, which are the same but for objects.

**Rest properties**:

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

**Spread properties** allow us to create a new object by combining the properties of the object passed after the spread operator:

```
const items = { first, second, ...others }
items //{ first: 1, second: 2, third: 3, fourth: 4, fifth: 5 }
```

### Set

A Set data structure allows us to add data to a container.

A Set is a collection of objects or primitive types (strings, numbers or booleans), and you can think of it as a Map where values are used as map keys, with the map value always being a boolean true.

#### Initialize a Set

A Set is initialized by calling:

```
const s = new Set()
```

#### Add items to a Set

You can add items to the Set by using the `add` method:

```
s.add('one')
s.add('two')
```

A set only stores unique elements, so calling `s.add('one')` multiple times won't add new items.

You can’t add multiple elements to a set at the same time. You need to call `add()` multiple times.

#### Check if an item is in the set

Once an element is in the set, we can check if the set contains it:

```
s.has('one') //true
s.has('three') //false
```

#### Delete an item from a Set by key

Use the `delete()` method:

```
s.delete('one')
```

#### Determine the number of items in a Set

Use the `size` property:

```
s.size
```

#### Delete all items from a Set

Use the `clear()` method:

```
s.clear()
```

#### Iterate the items in a Set

Use the `keys()` or `values()` methods - they are equivalent:

```
for (const k of s.keys()) {
  console.log(k)
}
for (const k of s.values()) {
  console.log(k)
}
```

The `entries()` method returns an iterator, which you can use like this:

```
const i = s.entries()
console.log(i.next())
```

calling `i.next()` will return each element as a `{ value, done = false }`object until the iterator ends, at which point `done` is `true`.

You can also use the forEach() method on the set:

```
s.forEach(v => console.log(v))
```

or you can just use the set in a for..of loop:

```
for (const k of s) {
  console.log(k)
}
```

#### Initialize a Set with values

You can initialize a Set with a set of values:

```
const s = new Set([1, 2, 3, 4])
```

#### Convert the Set keys into an array

```
const a = [...s.keys()]
// or
const a = [...s.values()]
```

#### A WeakSet

A WeakSet is a special kind of Set.

In a Set, items are never garbage collected. A WeakSet instead lets all its items be freely garbage collected. Every key of a WeakSet is an object. When the reference to this object is lost, the value can be garbage collected.

Here are the main differences:

1. you cannot iterate over the WeakSet
2. you cannot clear all items from a WeakSet
3. you cannot check its size

A WeakSet is generally used by framework-level code, and only exposes these methods:

- add()
- has()
- delete()

### Map

A Map data structure allows us to associate data to a key.

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

由于不知道写入内存部分需要多长的周期来广播，因此在读取值时，任何类型的写入操作都会完成，`Atomics` 可以避免竞争条件的发生。

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

**展开属性** 允许通过组合在展开运算符之后传递的对象属性而创建新对象：

```javascript
const items = { first, second, ...others }
items //{ first: 1, second: 2, third: 3, fourth: 4, fifth: 5 }
```

### 异步迭代器

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

这个新功能扩展了unicode字符，引入了 `\p{}` 来处理

任何 unicode 字符都有一组属性，例如 `script` 确认语言，`ASCII` 是一个布尔值用于检查 ASCII 字符。你可以将此属性方在() 中，正则表达式将来检查是否为真。 

```javascript
/^\p{ASCII}+$/u.test('abc')   //✅
/^\p{ASCII}+$/u.test('ABC@')  //✅
/^\p{ASCII}+$/u.test('ABC🙃') //❌
```

`ASCII_Hex_Digit` 是另一个布尔值，用于检查字符串是否包含有效的十六进制数字：

```javascript
/^\p{ASCII_Hex_Digit}+$/u.test('0123456789ABCDEF') //✅
/^\p{ASCII_Hex_Digit}+$/u.test('h')                //❌
```

此外，还有很多其他的属性。你可以在()中添加它们的名字来检查它们，包括 `Uppercase`, `Lowercase`, `White_Space`, `Alphabetic`, `Emoji`等等：

```javascript
/^\p{Lowercase}$/u.test('h') //✅
/^\p{Uppercase}$/u.test('H') //✅
/^\p{Emoji}+$/u.test('H')   //❌
/^\p{Emoji}+$/u.test('🙃🙃') //✅
```

除了二进制属性外，你还可以检查任何 unicode 字符属性以匹配特定的值，在这个例子中，我检查字符串是用希腊语还是拉丁字母写的：

```javascript
/^\p{Script=Greek}+$/u.test('ελληνικά') //✅
/^\p{Script=Latin}+$/u.test('hey') //✅
```

阅读[ttps://github.com/tc39/proposal-regexp-unicode-property-escapes](ttps://github.com/tc39/proposal-regexp-unicode-property-escapes) 获取使用所有属性的详细信息。

#### Named capturing groups

In ES2018 a capturing group can be assigned to a name, rather than just being assigned a slot in the result array:

```javascript
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

有时候我们并不需要将参数绑定到 try/catch 中。

在以前我们不得不这样做：

```javascript
try {
  //...
} catch (e) {
  //handle error
}
```

即使我们从来没有通过 `e` 来分析错误，但现在我们可以简单的省略它：

```javascript
try {
  //...
} catch {
  //handle error
}
```

### Object.fromEntries()

Objects have an `entries()` method, since ES2017.

从 ES2017 开始 Object将有一个 `entries()` 方法。

它将返回一个包含所有对象自身属性的数组的数组，如`[key, value]`：

```javascript
const person = { name: 'Fred', age: 87 }
Object.entries(person) // [['name', 'Fred'], ['age', 87]]
```

ES2019 引入了一个新的 `Object.fromEntries()` 方法，它可以从上述的属性数组中创建一个新的对象：

```javascript
const person = { name: 'Fred', age: 87 }
const entries = Object.entries(person)
const newPerson = Object.fromEntries(entries)

person !== newPerson //true 
```

### String.prototype.{trimStart,trimEnd}

这些功能已经被 v8/Chrome 实现了近一年的时间，它将在 ES2019 中实现标准化。

#### `trimStart()`

删除字符串首部的空格并返回一个新的字符串：

```javascript
'Testing'.trimStart() //'Testing'
' Testing'.trimStart() //'Testing'
' Testing '.trimStart() //'Testing '
'Testing'.trimStart() //'Testing'
```

#### `trimEnd()`

删除字符串尾部的空格并返回一个新的字符串：

```javascript
'Testing'.trimEnd() //'Testing'
' Testing'.trimEnd() //' Testing'
' Testing '.trimEnd() //' Testing'
'Testing '.trimEnd() //'Testing'
```

### Symbol.prototype.description

现在你可以使用 `description` 来获取 Symbol 的值，而不必使用 `toString()` 方法：

```javascript
const testSymbol = Symbol('Test')
testSymbol.description // 'Test'
```

### JSON improvements

在此之前 JSON 字符串中不允许使用分隔符（\u2028）和分隔符（\u2029）。

使用 JSON.parse 时，这些字符会导致一个 `SyntaxError` 错误，但现在它们可以正确的解析并如 JSON 标准定义的那样。

### Well-formed JSON.stringify()

修复 `JSON.stringify()` 在处理 UTF-8 code points (U+D800 to U+DFFF)。

在修复之前，调用 `JSON.stringify()` 将返回格式错误的 Unicode 字符，如（a "�")。

现在你可以安全放心的使用 `JSON.stringify()` 转成字符串，也可以使用 `JSON.parse()` 将它转换回原始表示的形态。

### Function.prototype.toString()

函数总会有一个 `toString` 方法，它将返回一个包含函数代码的字符串。

ES2019 对返回值做了修改，以避免剥离注释和其他字符串（如：空格），将更准确的表示函数的定义。

If previously we had

以前也许我们这样过：

```javascript
function /* this is bar */ bar () {}
```

当时的行为：

```
bar.toString() //'function bar() {}
```

现在的行为：

```
bar.toString(); // 'function /* this is bar */ bar () {}'
```

------

总结一下，我希望这篇文章可以帮助你了解一些最新的 JavaScript 以及我们在 2019 年即将看见的内容。

[**Click here to get a PDF / ePub / Mobi version of this post to read offline**](https://flaviocopes.com/es5-to-next/)