## 块级作用域：let和const
const 是 ES6 中用于声明变量的新关键字。 const  比 var 更强大。使用后，无法重新分配变量。换句话说，它是一个不可变的变量，除非它与对象一起使用。

这对于定位选择器非常有用。例如，当我们有一个触发事件的按钮时，或者当您想在 JavaScript 中选择 HTML 元素时，请使用 const 而不是 var。这是因为 var 会被提升，当不想重新分配变量时，最好使用 const。<br/>
**在下面的代码中，const 不会更改，也不能重新分配。如果您尝试为其赋予新值，则会返回错误。**
```
// ES5
var MyBtn = document.getElementId('mybtn');

// ES6
const MyBtn = document.getElementById('mybtn');
```
let 可以重新分配并获得新的价值。它创建了一个可变变量。<br/>
let 与 const 相同，因为两者都是块级作用域，这意味着该变量仅在其块级范围内可用。

```
let name = "Said";
    name = "Rick";
console.log(name); // Rick
```


## 箭头代码
```
// ES5
function myFunc(name) {
  return 'Hello ' + name;
}
console.log(myFunc('said'));  // Hello said
```
```
// ES6 Arrow function
const myFunc = name => {
  return `Hi ${name}`;
}
console.log(myFunc('Said')); // Hi Said

// 或者不要 return 关键字
const myFunc = name => `Hi ${name}`;

console.log(myFunc('Said'));// Hi Said
```

此外，可以使用箭头功能与 map，filter 和 reduce 内置函数。

```
const myArray = ['tony', 'Sara', 'Said', 5];

// ES5
let Arr1 = myArray.map(function(item) {
  return item;
});
console.log(Arr1);// ["tony", "Sara", "Said", 5]

// ES6
let Arr2 = myArray.map(item => item);
console.log(Arr2);// ["tony", "Sara", "Said", 5]
```

## 模板字符串
当我们想在字符串中使用变量时我们不必使用加号（+）运算符来连接字符串。
```
// ES5
function myFunc1(name, age) {
  return 'Hi ' + name + ' Your age is ' + age + ' year old';
}
console.log(myFunc('Said', 22)); // Hi Said, Your age is 22 year old
```
```
// ES6
const myFunc = (name, age) => {
  return `Hi ${name}, Your age is ${age} year old`;
}
// or
const myFunc = (name, age) => `Hi ${name}, Your age is ${age} year old`;

console.log(myFunc1('Said', 22)); // Hi Said, Your age is 22 year old
```

## 默认参数
当您忘记编写参数时，它不会返回未定义的错误，因为该参数已在默认值中定义。因此，当您使用遗漏参数运行函数时，它将采用默认参数的值，并且不会返回错误！
<br/>
看看这个例子：
```
const myFunc = (name, age) => `Hi ${name}, Your age is ${age} year old`;

console.log(myFunc('Said')); // Hi Said, Your age is undefined year old
```
上面的函数返回 undefined，因为我们忘了给它第二个参数 age。<br/>
但是如果我们使用默认参数，当我们忘记分配参数时,它将使用它的默认值，将不会返回 undefined！
```
const myFunc = (name, age = 22) => `Hi ${name}, Your age is ${age} year old`;

console.log(myFunc('Said')); // Hi Said, Your age is 22 year old
```
如您所见，即使我们错过了第二个参数，该函数也会返回一个值。现在使用默认参数我们可以提前处理错误。

## 数组和对象解构
解构使得将数组或对象的值分配给新变量更容易。

旧语法：
```
const contacts = {
  name: 'said',
  famillyName: 'Hayani',
  age: 22
};

let name = contacts.name;
let famillyName = contacts.famillyName;
let myAge = contacts.age;

console.log(name); // said
console.log(famillyName); // Hayani
console.log(myAge); // 22
```
ES6 新语法：
```
const contacts = {
  name: 'said',
  famillyName: 'Hayani',
  age: 22
};

let {name, famillyName, age} = contacts;

console.log(name); // said
console.log(famillyName); // Hayani
console.log(age); // 22
```
使用 ES5，我们必须为每个变量分配每个值。使用 ES6，我们只需将我们的值放在大括号中以获取对象的任何属性。<br/>
注意：如果指定的变量与属性名称不同，则返回 undefined。例如，如果属性的名称是 name，我们将其分配给 username变量，它将返回undefined。<br/>
我们总是必须将变量命名为与属性名称相同。但是如果我们想要重命名变量，我们可以使用冒号：代替。<br/>

```
const contacts = {
  name: 'said',
  famillyName: 'Hayani',
  age: 22
};

let {name:otherName, famillyName, myAge} = contacts;

console.log(otherName);// said
```
对于数组，我们使用与对象相同的语法。我们只需用方括号替换花括号。
```
const Arr = ['Lionel', 'John', 'Layla', 20];

let [value1, value2, value3] = Arr;
console.log(value1); // Lionel
console.log(value2); // John
console.log(value3); // Layla
```
## ES6 模块:Import和export
在 JavaScript 应用程序中使用 import 和 export 使其更强大。它们允许您创建单独的可重用组件。<br/>
如果您熟悉任何 JavaScript MVC 框架，您将看到他们使用 import 和 export 出来在大多数时间处理组件。那么它们如何真正起作用呢？<br/>
很简单！ export 允许您导出要在另一个 JavaScript 组件中使用的模块。我们使用 import 导入该模块以在我们的组件中使用它。<br/>
例如，我们有两个文件。第一个名为 detailComponent.js，第二个名为 homeComponent.js。<br/>
在 detailComponent.js 中，我们将导出 detail 函数。<br/>
```
// ES6 
export default function detail(name, age) {
  return `Hello ${name}, your age is ${age} year old!`;
}
```
如果我们想在 homeComponent.js 中使用此函数，我们将只使用 import
```
import { detail } from './detailComponent';

console.log(detail('Said', 20)); // Hello Said, your age is 20 year old!
```
如果我们要导入多个模块，我们只需将它们放在大括号内。

```
import {detail, userProfile, getPosts} from './detailComponent';
console.log(detail('Said', 20)); 
console.log(userProfile); 
console.log(getPosts));
```
## 编写异步代码:promis

Promise 是 ES6 的新功能。这是编写异步代码的方法。例如，当我们想要从 API 获取数据时，可以使用它，或者当我们有一个需要时间执行的函数时。
Promise 使解决问题更容易，所以让我们创建我们的第一个 Promise！
```
const myPromise = () => {
  return new Promise((resolve, reject) => {
    resolve('Hi the Promise execute successfully');
  })
}
console.log(myPromise()); // Promise {<resolved>: "Hi the Promise execute successfully"}
```
如果您登录控制台，它将返回一个 Promise。因此，如果我们想在获取数据后执行一个函数，我们将使用 Promise。 Promise有两个参数： resolve 和 reject 来处理预期的错误。<br/>
注意：fetch函数返回一个Promise本身！
```
const url='https://jsonplaceholder.typicode.com/posts';
const getData=(url)=>{
  return fetch(url);
}
getData(url).
then(data=> data.json()).
then(result=> console.log(result));
```
现在，如果您登录控制台，它将返回一个数据数组。
## Rest 参数和 Spread 运算符
Rest 参数用于获取数组的参数，并返回一个新数组。
```
const arr = ['said', 20, 'Javascript enthusiast', 'Hi', 'Said', 'How are you?'];

// 通过解构获取值
const [val1, val2, val3, ...rest] = arr;

const Func = (restOfArr) => {
  return restOfArr.filter(item => {return item}).join(" ");
}

console.log(Func(rest)); // Hi Said How are you?
const arr = ['said', 20, 'Javascript enthusiast', 'Hi', 'Said', 'How are you?'];

const Func = (...anArray) => anArray;

console.log(Func(arr)); //  ['said', 20, 'Javascript enthusiast', 'Hi', 'Said', 'How are you?']
```
spread 运算符与 rest 参数具有相同的语法，但是 spread 运算符采用数组本身而不仅仅是参数。我们可以使用 Spread 参数来获取数组的值，而不是使用 for 循环或任何其他方法。
```
const arr=['said',20,'JavaScript enthusiast','Hi','Said','How are you?'];
const Func=(...anArray)=>{
  return anArray;
}
console.log(Func(arr)); //["said", 20, "JavaScript enthusiast", "Hi", "Said", "How are you?"
```
## class
类是面向对象编程（OOP）的核心。它们使您的代码更安全和封装。使用类可以为代码提供一个很好的结构并使其保持面向对象。

```
class myClass {
  constructor() {
  }
}
```
要创建一个类，请使用 class 关键字，后跟带有两个大括号的类的名称。
```
class myClass {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}

const user = new myClass('Said', 22);
console.log(user.name); // Said
cosnole.log(user.age); // 22
```
现在我们可以使用 new 关键字访问类方法和属性。
```
class myClass{
    constructor(name,age){
    this.name=name;
    this.age=age;
}
}
const Home= new myClass("said",20);
console.log(Home.name)//  said
```
现在我们可以使用 new 关键字访问类方法和属性。
```
class myClass{
    constructor(name,age){
    this.name=name;
    this.age=age;
}
}
const Home= new myClass("said",20);
console.log(Home.name)//  said
```
要从其他类继承，请使用 extends 关键字，后跟要继承的类的名称。
```
class myClass {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  sayHello() {
    cosnole.log(`Hi ${this.name} your age is ${this.age} `);
  }
}

// 继承 myClass 方法和属性
class UserProfile extends myClass {
  username() {
    console.log(this.name);
  }
}

const profile = new UserProfile('Said', 22);
profile.sayHello();// Hi Said your age is 22;
profile.username();// Said
```
