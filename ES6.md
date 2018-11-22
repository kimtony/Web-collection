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
