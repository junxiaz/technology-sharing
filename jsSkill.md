### 1. If 多个条件的时候
有时候你会经常判断一个变量是否等于多个值的情况：
```
// bad
if (x === 'abc' || x === 'def' || x === 'ghi' || x ==='jkl') {
}


// good
if (['abc', 'def', 'ghi', 'jkl'].includes(x)) {
}
```

### 2. If true … else
if else? 还不如用三元运算符
```
// bad
let test: boolean;
if (x > 100) {
  test = true;
} else {
  test = false;
}

// good
let test = (x > 10) ? true : false;
// 或者更简单的
let test = x > 10;
console.log(test);
三元运算符还可以嵌套，像下面这样：

let x = 300,
let test2 = (x > 100) ? 'greater 100' : (x < 50) ? 'less 50' : 'between 50 and 100';
console.log(test2); // "greater than 100"
```
但是不建议嵌套太多层的（超过两层就没必要使用三元运算符了）。


### 3. Null, Undefined, 空检查
前面有空值，如何判断？
```
// bad
if (first !== null || first !== undefined || first !== '') {
  let second = first;
}

// good
let second = first || '';
```
### 4. Null Value 检查与分配默认值
```
let first = null,
let second = first || '';
console.log("null check", second); // second为 ""
```

### 5. Undefined 检查与分配默认值
```
let first= undefined,
let second = first || '';
console.log("undefined check", second); // second为 ""
```

### 6.foreach 循环
如何更好的迭代？
```
// bad
for (var i = 0; i < testData.length; i++)

// good
for (let i in testData) 或 for (let i of testData)
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
// bad
let test;
function checkReturn() {
  if (!(test === undefined)) {
    return test;
  } else {
    return callMe('test');
  }
}
var data = checkReturn();
console.log(data); // test
function callMe(val) {
  console.log(val);
}

// good
function checkReturn() {
  return test || callMe('test');
}
```
### 8. 函数调用简单的方式
用三元运算符解决函数调用
```
// bad
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


// good
(test3 === 1? test1:test2)();
```


### 9. Switch
switch 有时候太长？可以优化下
```
// bad
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



// good
var data = {
  1: test1,
  2: test2,
  3: test
};

data[anything] && data[anything]();
```

### 10. 多行字符串速记
字符串多行时，如何更好的处理？用 + 号？
```
//bad
const data = 'abc abc abc abc abc abc\n\t'
+ 'test test,test test test test\n\t'



//good
const data = `abc abc abc abc abc abc
test test,test test test test`
```

### 11. 隐式返回缩写法
当用剪头函数时，有个隐式返回，注意括号。
```
bad:
//bad
function getArea(diameter) {
  return Math.PI * diameter
}
//good
getArea = diameter => (
  Math.PI * diameter;
)
```

### 12.Lookup Conditions good
如果我们有代码来检查类型，并且基于类型需要调用不同的方法，我们可以选择使用多个 else if 进行切换，但是如果我们有比这更好的方式呢？
```
// bad
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

// good
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


/** 输出:
[ [ 'test1', 'abc' ],
[ 'test2', 'cde' ],
[ 'test3', 'efg' ]
]
**/
```
### 14. Object.values()
这也是 ES8 中引入的一项新功能，它执行与 Object.entries () 类似的功能，但没有key部分:
```
const data = { test1: 'abc', test2: 'cde' };
const arr = Object.values(data);
console.log(arr);


/** 输出:
[ 'abc', 'cde']
**/
```

### 15. 多次重复字符串
为了一次又一次地重复相同的字符，我们可以使用 for 循环并将它们添加到同一个循环中，也可以：
```
//bad
let test = '';
for(let i = 0; i < 5; i ++) {
  test += 'test ';
}
console.log(str); // test test test test test


//good
'test '.repeat(5);
```
### 16.指数幂函数
数学指数幂函数的速记:
```
//bad
Math.pow(2,3); // 8

//good
2**3 // 8
```

### 17. 数字分隔符
现在，您只需使用 _ 即可轻松分隔数字。
```
// bad
let number = 98234567


// good
let number = 98_234_567
```

### 18. Array.find 缩写法
当我们需要在一个对象数组中按属性值查找特定对象时，find 方法很有用
```
// bad
const data = [{
        type: 'test1',
        name: 'abc'
    },
    {
        type: 'test2',
        name: 'cde'
    },
    {
        type: 'test1',
        name: 'fgh'
    },
]
function findtest1(name) {
    for (let i = 0; i < data.length; ++i) {
        if (data[i].type === 'test1' && data[i].name === name) {
            return data[i];
        }
    }
}
// good
const filteredData = data.find(data => data.type === 'test1' && data.name === 'fgh');
console.log(filteredData); // { type: 'test1', name: 'fgh' }
```
### 19. 解构赋值缩写法
```
// bad
const test1 = this.data.test1;
const test2 = this.data.test2;
const test2 = this.data.test3;
// good
const { test1, test2, test3 } = this.data;
```
### 20. 对象属性的赋值
```
let test1 = 'a';
let test2 = 'b';
// bad
let obj = {test1: test1, test2: test2};
// good
let obj = {test1, test2};
```
### 21.字符串转换为数字
```
// bad
let test1 = parseInt('123');
let test2 = parseFloat('12.3');
// good
let test1 = +'123';
let test2 = +'12.3';
```
### 22. 默认参数值
```
// bad
function add(test1, test2) {
  if (test1 === undefined)
    test1 = 1;
  if (test2 === undefined)
    test2 = 2;
  return test1 + test2;
}
// good
add = (test1 = 1, test2 = 2) => (test1 + test2);add() // 3
```
