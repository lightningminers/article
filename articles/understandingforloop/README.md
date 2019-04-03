---
type: FrontEnd
title: Understanding the For…of Loop In JavaScript
link: https://blog.bitsrc.io/understanding-the-for-of-loop-in-javascript-8aded97d7ef8
author: [kurtwanger40](https://blog.bitsrc.io/@kurtwanger40)
---

InJavaScript, we have so many looping statements:

- `while` statement
- `do...while` statement
- `for` statement
- `for...in` statement
- `for...of` statement

All these have one basic function: they repeat until a certain condition is met.

In this article, we will look into the `for...of` statement to see how it works and where it can be used to write better code in our JS applications.

**Tip**: Build JS apps faster with [**Bit** (open-source)](https://github.com/teambit/bit). It lets you quickly discover, share and install components/modules across your apps. Give it a try.



![img](https://cdn-images-1.medium.com/max/1600/1*Yhkh7jbS5Mx9uP96Y88pZg.gif)

React spinner components: choose, learn use.

[**Component Discovery and Collaboration · Bit**
*Bit is where developers share components and collaborate to build amazing software together. Discover components shared…*bit.dev](https://bit.dev/)

### for…of

`for...of` is a type of `for` statement to cycles through `iterables(iterable objects)` until it reaches the end of the line.

Let’s look at a basic example:

```
let arr = [2,4,6,8,10]
for(let a of arr) {
    log(a)
}
// It logs:
// 2
// 4
// 6
// 8
// 10
```

With much less code than the `for` statement, we looped through the `arr`array.

```
let myname = "Nnamdi Chidume"
for (let a of myname) {
    log(a)
}
// It logs:
// N
// n
// a
// m
// d
// i
//
// C
// h
// i
// d
// u
// m
// e
```

You know if we used for loop, we will have to employ some mathematics and logic to know when we reached the end of `myname` and quit. But you see with for..of loop we save ourselves some headache :).

As we can see `for...of` has the following general definition:

```
for ( variable of iterable) {
    //...
}
```

`variable` - holds the value of each property of the iterable on each iteration. `iterable` - is the object to be iterated upon.

### Iterables and Iterator

At the definition of for…of loop, we said it “cycles through *iterables(iterable objects)*”. So with this, it means to tell us that `for...of` loop could not be used unless the item it is going to try to loop over is an iterable.

Then, what are iterables?

Simply put, Iterables are objects that iteration could be performed on. In ECMAScript 2015 a coupla additions were made. These additions were new protocols. And among the protocols were the Iterator protocol and Iterable protocol.

According to Mozilla Developer, “The iterable protocol allows JavaScript objects to define or customize their iteration behavior, such as what values are looped over in a for..of construct.” and “In order to be iterable, an object must implement the `@@iterator` method, meaning that the object (or one of the objects up its prototype chain) must have a property with a `@@iterator` key which is available via constant `Symbol.iterator`."

What this actually means is that, for your objects to be able to be looped through by `for...of` it must be iterable in other words it must have the weird `@@iterator` as property. That's conforming to the iterable protocol.

So when the object with the `@@iterator` property is to be iterated by `for...of`, the @@iterator method is called by the same `for...of`. The @@iterator must return an iterator.

Now, the Iterator protocol defines a way by which a stream of values could be returned from an object. An iterator must implement the `next` method. The next method has a set of rules to follow:

- It must return an object with properties done, value {done, value}
- The done is Boolean that denotes when the end of the stream is reached.
- The value holds the value of the current cycle.

Example:

```
const createIterator = function () {
    var array = ['Nnamdi','Chidume']
    return  {
        next: function() {
            if(this.index == 0) {
                this.index++
                return { value: array[this.index], done: false }
            }
            if(this.index == 1) {
                return { value: array[this.index], done: true }
            }
        },
        index: 0
    }
}
const iterator = createIterator()
log(iterator.next()) // Nnamdi
log(iterator.next()) // Chidume
```

Basically, the @@iterator method returns an iterator which the `for...of`uses to cycle through the implementing object to get the values. So, if an object doesn't have the `@@iterator` method and/or returns an iterator, the `for...of` statement on it won't work.

```
const nonIterable = //...
 for( let a of nonIterable) {
     // ...
 }
for( let a of nonIterable) {
               ^
TypeError: nonIterable is not iterable
```

Examples of Iterables are:

- String
- Map
- TypedArray
- Array
- Set
- Generator

Notice that Object is missing. Object is not an iterable. If we try to use loop through an object’s properties using the for…of loop:

```
let obj {
    firstname: "Nnamdi",
    surname: "Chidume"
}
for(const a of obj) {
    log(a)
}
```

It will throw an error:

```
for(const a of obj) {
               ^
TypeError: obj is not iterable
```

We can check if an object is iterable by doing this:

```
const str = new String('Chidume');
log(typeof str[Symbol.iterator]);
function
```

See, it logs a `function`, that shows @@iterator property is present in String. If we try Object:

```
const obj = {
    surname: "Chidume"
}
log(typeof obj[Symbol.iterator]);
undefined
```

Woo!! `undefined` means not present.

### for…of: Array

An Array is an iterable.

```
log(typeof new Array("Nnamdi", "Chidume")[Symbol.iterator]);
// function
```

That’s why we can perform `for...of` on it.

```
const arr = ["Chidume", "Nnamdi", "loves", "JS"]
for(const a of arr) {
    log(a)
}
// It logs:
// Chidume
// Nnamdi
// loves
// JS
const arr = new Array("Chidume", "Nnamdi", "loves", "JS")
for(const a of arr) {
    log(a)
}
// It logs:
// Chidume
// Nnamdi
// loves
// JS
```

### for…of: String

String is also iterable.

```
const myname = "Chidume Nnamdi"
for(const a of myname) {
    log(a)
}
// It logs:
// C
// h
// i
// d
// u
// m
// e
//
// N
// n
// a
// m
// d
// i
const str = new String("The Young")
for(const a of str) {
    log(a)
}
// It logs:
// T
// h
// e
//
// Y
// o
// u
// n
// g
```

### for…of: Map

```
const map = new Map([["surname", "Chidume"],["firstname","Nnamdi"]])
for(const a of map) {
    log(a)
}
// It logs:
// ["surname", "Chidume"]
// ["firstname","Nnamdi"]
for(const [key, value] of map) {
    log(`key: ${key}, value: ${value}`)
}
// It logs:
// key: surname, value: Chidume
// key: firstname, value: Nnamdi
```

### for…of: Set

```
const set = new Set(["Chidume","Nnamdi"])
for(const a of set) {
    log(a)
}
// It logs:
// Chidume
// Nnamdi
```

### for…of: TypedArray

```
const typedarray = new Uint8Array([0xe8, 0xb4, 0xf8, 0xaa]);
for (const a of typedarray) {
  log(a);
}
// It logs:
// 232
// 180
// 248
// 170
```

### for…of: arguments

arguments is iterable? Well, let’s check it out:

```
// testFunc.js
function testFunc(arg) {
    log(typeof arguments[Symbol.iterator])
}
testFunc()
$ node testFunc
function
```

Well, that settles it. If we investigate further, arguments is actually of type IArguments and the class implementing the IArguments interface has the @@iterator property which makes arguments iterable.

```
// testFunc.js
function testFunc(arg) {
    log(typeof arguments[Symbol.iterator])
    for(const a of arguments) {
        log(a)
    }
}
testFunc("Chidume")
// It:
// Chidume
```

### for…of: Custom Iterables

Like we demonstrated in the previous sections we can create a custom iterable that can be iterated by `for..of`.

```
var obj = {}
obj[Symbol.iterator] = function() {
    var array = ["Chidume", "Nnamdi"]
    return {
        next: function() {
            let value = null
            if (this.index == 0) {
                value = array[this.index]
                this.index++
                    return { value, done: false }
            }
            if (this.index == 1) {
                value = array[this.index]
                this.index++
                    return { value, done: false }
            }
            if (this.index == 2) {
                return { done: true }
            }
        },
        index: 0
    }
};
```

I created an object `obj` and to make it iterable, I assigned a `@@iterator`property to it using the `[Symbol.iterator]`. Then, I made the function to return an iterator.

```
//...
return {
    next: function() {...}
}
//...
```

Remember, an iterator must have a `next()` function.

Inside the next function, I implemented the values will be returning to for..of during iteration. Looking at it above, you will see that what I did is quite clear.

Let’s test this our `obj` against a for..of to see what will happen:

```
// customIterableTest.js
//...
for (let a of obj) {
    log(a)
}
$ node customIterableTest
Chidume
Nnamdi
```

Yea!!! You see it worked!

### Making Object and plain objects iterable

Plain objects are not iterable and also objects from `Object` are not iterable.

We can by-pass this by adding @@iterator to the Object.prototype with a custom iterator.

```
Object.prototype[Symbol.iterator] = function() {
    let properties = Object.keys(this)
    let count = 0
    let isdone = false
    let next = () => {
        let value = this[properties[count]]
        if (count == properties.length) {
            isdone = true
        }
        count++
        return { done: isdone, value }
    }
    return { next }
}
```

The `properties` variable holds the properties of the object gotten using the `Object.keys()` call. In the next function, we simply return each value from the properties variable and update the count so as to get the next value from the properties variable using the count variable as the index. When the count equals the length of the properties we set done to true, so the iteration stops.

Testing using Object:

```
let o = new Object()
o.s = "SK"
o.me = 'SKODA'
for (let a of o) {
    log(a)
}
SK
SKODA
```

It works!!!

With plain objects:

```
let dd = {
    shit: 900,
    opp: 800
}
for (let a of dd) {
    log(a)
}
900
800
```

Tada!! :)

So we can add this as a polyfill so we can use for..of on objects where ever we want in our app.

### Using for…of on ES6 classes

We can use for..of to iterate through a list of data in an instance of a class.

```
class Profiles {
    constructor(profiles) {
        this.profiles = profiles
    }
}
const profiles = new Profiles([
    {
        firstname: "Nnamdi",
        surname: "Chidume"
    },
    {
        firstname: "Philip",
        surname: "David"
    }
])
```

The class Profiles has a property `profile` that holds an array of users. We may need to display this data in our app using for...of. If we do this:

```
//...
for(const a of profiles) {
    log(a)
}
```

Obviously, it won’t work

```
for(const a of profiles) {
               ^
TypeError: profiles is not iterable
```

To make `profiles` iterable remember the rules:

- The object must have the `@@iterator` property.
- The `@@iterator` function must return an iterator.
- The `iterator` must implement the `next()` function.

We define the @@iterator property using the familiar constant `[Symbol.iterator]`.

```
class Profiles {
    constructor(profiles) {
            this.profiles = profiles
        }
        [Symbol.iterator]() {
            let props = this.profiles
            let propsLen = this.profiles.length
            let count = 0
            return {
                next: function() {
                    if (count < propsLen) {
                        return { value: props[count++], done: false }
                    }
                    if (count == propsLen) {
                        return { done: true }
                    }
                }
            }
        }
}
```

Then, if we run:

```
//...
for(const a of profiles) {
    log(a)
}
$ node profile.js
{ firstname: 'Nnamdi', surname: 'Chidume' }
{ firstname: 'Philip', surname: 'David' }
```

We have our profiles property displayed.

### Async Iterator

A new construct was introduced to ECMAScript 2018 to be able to loop through an array of Promises, this new construct is `for-await-of` and a new Symbol `Symbol.asyncIterator`.

The `Symbol.asyncIterator` function in an iterable returns an iterator that returns a Promise.

```
const f = {
    [Symbol.asyncIterator]() {
        return new Promise(...)
    }
}
```

The difference between `[Symbol.iterator]` and `[Symbol.asyncIterator]` is that the former returns `{ value, done }` while the latter returns a `Promise`that resolves to `{ value, done }`.

Our f above will look like this:

```
const f = {
    [Symbol.asyncIterator]() {
        return {
            next: function() {
                if (this.index == 0) {
                    this.index++
                        return new Promise(res => res({ value: 900, done: false }))
                }
                return new Promise(res => res({ value: 1900, done: true }))
            },
            index: 0
        }
    }
}
```

The `f` is an async iterable. You see it always returns a Promise, the Promise has a resolve function that returns a value at each iteration.

To iterate through `f`, we will not use `for..of` rather we will use the new `for-await-of` like this:

```
// ...
async function fAsyncLoop(){
    for await (const _f of f) {
        log(_f)
    }
}
fAsyncLoop()
$ node fAsyncLoop.js
900
```

We can also use this `for-await-of` to loop through an array of Promises:

```
const arrayOfPromises = [
    new Promise(res => res("Nnamdi")),
    new Promise(res => res("Chidume"))
]
async function arrayOfPromisesLoop(){
    for await (const p of arrayOfPromises) {
        log(p)
    }
}
arrayOfPromisesLoop()
$ node arrayOfPromisesLoop.js
Nnamdi
Chidume
```

### Conclusion

In this post we dug deep into `for...of`loop. We started by defining what for..of is, and went on to see what makes what iterable. Then, we looked at the complete list of iterables in JS and went through each of them to see how to work with `for...of` loop on them.

Like I said in the beginning, for..of saves us a lot of complexities and logic and helps make our code looks cleaner and readable. If you haven’t tried this awesome for- loop mutation, I think now will be the right time to do so.

If you have any question regarding this or anything I should add, correct or remove, feel free to comment below, and anything or DM me. Thanks for reading! :)
