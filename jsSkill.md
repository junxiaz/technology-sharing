### 1. If 多个条件的时候
有时候你会经常判断一个变量是否等于多个值的情况：
```
//longhand
if (x === 'abc' || x === 'def' || x === 'ghi' || x ==='jkl') {
    //logic
}


//shorthand
if (['abc', 'def', 'ghi', 'jkl'].includes(x)) {
   //logic
}
```

### 2. If true … else
if else? 还不如用三元运算符
```
// Longhand
let test: boolean;
if (x > 100) {
    test = true;
} else {
    test = false;
}

// Shorthand
let test = (x > 10) ? true : false;
//or we can simply use
let test = x > 10;
console.log(test);
三元运算符还可以嵌套，像下面这样：

let x = 300,
let test2 = (x > 100) ? 'greater 100' : (x < 50) ? 'less 50' : 'between 50 and 100';
console.log(test2); // "greater than 100"
```
但是不建议嵌套太多层的。


### 3. Null, Undefined, 空检查
前面有空值，如何判断？
```
// Longhand
if (first !== null || first !== undefined || first !== '') {
    let second = first;
}

// Shorthand
let second = first|| '';
```
### 4. Null Value 检查与分配默认值
```
let first = null,
let second = first || '';
console.log("null check", test2); // output will be ""
```

### 5. Undefined 检查与分配默认值
```
let first= undefined,
let second = first || '';
console.log("undefined check", test2); // output will be ""
```

### 6.foreach 循环
如何更好的迭代？
```
// Longhand
for (var i = 0; i < testData.length; i++)

// Shorthand
for (let i in testData) 或  for (let i of testData)
```
上面 let i in 或 let i of 是比较好的方式，

或者下面这样：使用 forEach
```
function testData(element, index, array) {
  console.log('test[' + index + '] = ' + element);
}


[11, 24, 32].forEach(testData);
// prints: test[0] = 11, test[1] = 24, test[2] = 32
```
### 7. 比较返回
在 return 语句中使用比较将避免我们的 5 行代码，并将它们减少到 1 行。
```
// Longhand
let test;
function checkReturn() {
    if (!(test === undefined)) {
        return test;
    } else {
        return callMe('test');
    }
}
var data = checkReturn();
console.log(data); //output test
function callMe(val) {
    console.log(val);
}

// Shorthand
function checkReturn() {
    return test || callMe('test');
}
```
### 8. 函数调用简单的方式
用三元运算符解决函数调用
```
// Longhand
function test1() {
  console.log('test1');
};
function test2() {
  console.log('test2');
};
var test3 = 1;
if (test3 == 1) {
  test1();
} else {
  test2();
}


// Shorthand
(test3 === 1? test1:test2)();
```


### 9. Switch
switch 有时候太长？看看能不能优化
```
// Longhand
switch (data) {
  case 1:
    test1();
  break;

  case 2:
    test2();
  break;

  case 3:
    test();
  break;
  // And so on...
}



// Shorthand
var data = {
  1: test1,
  2: test2,
  3: test
};

data[anything] && data[anything]();
```

### 10. 多行字符串速记
字符串多行时，如何更好的处理？用 +  号？
```
//longhand
const data = 'abc abc abc abc abc abc\n\t'
    + 'test test,test test test test\n\t'



//shorthand
const data = `abc abc abc abc abc abc
         test test,test test test test`
```

### 11.Implicit Return Shorthand
当用剪头函数时，有个隐式返回，注意括号。
```
Longhand:
//longhand
function getArea(diameter) {
  return Math.PI * diameter
}
//shorthand
getArea = diameter => (
  Math.PI * diameter;
)
```

### 12.Lookup Conditions Shorthand
如果我们有代码来检查类型，并且基于类型需要调用不同的方法，我们可以选择使用多个 else ifs 或进行切换，但是如果我们有比这更好的方式呢？
```
// Longhand
if (type === 'test1') {
  test1();
}
else if (type === 'test2') {
  test2();
}
else if (type === 'test3') {
  test3();
}
else if (type === 'test4') {
  test4();
} else {
  throw new Error('Invalid value ' + type);
}



// Shorthand
var types = {
  test1: test1,
  test2: test2,
  test3: test3,
  test4: test4
};

var func = types[type];
(!func) && throw new Error('Invalid value ' + type); func();
```
### 13.Object.entries()

此功能有助于将对象转换为对象数组。
```
const data = { test1: 'abc', test2: 'cde', test3: 'efg' };
const arr = Object.entries(data);
console.log(arr);


/** Output:
[ [ 'test1', 'abc' ],
  [ 'test2', 'cde' ],
  [ 'test3', 'efg' ]
]
**/
```
### 14. Object.values()
这也是 ES8 中引入的一项新功能，它执行与 Object.Entry () 类似的功能，但没有关键部分:
```
const data = { test1: 'abc', test2: 'cde' };
const arr = Object.values(data);
console.log(arr);


/** Output:
[ 'abc', 'cde']
**/
```

### 15. 多次重复字符串
为了一次又一次地重复相同的字符，我们可以使用 for 循环并将它们添加到同一个循环中，但是如果我们有一个速记呢？
```
//longhand
let test = '';
for(let i = 0; i < 5; i ++) {
  test += 'test ';
}
console.log(str); // test test test test test


//shorthand
'test '.repeat(5);

### 16. 指数幂函数
数学指数幂函数的速记:

//longhand
Math.pow(2,3); // 8

//shorthand
2**3 // 8
```

### 17. 数字分隔符
现在，您只需使用 _ 即可轻松分隔数字。
```
//old syntax
let number = 98234567


//new syntax
let number = 98_234_567
```
