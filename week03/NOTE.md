# 每周总结可以写在这里
[浮点数转化](jsfiddle.net/pLh8qeor/19/)

# 表达式
语法部分 进行时

ecma 11.2 Left-Hand-Side Expressions

* Member
  * a.b
  * a[b] *和a.b不同的是这里的b可以是表达式*
  * foo\`string\`
  * super.b
  * super['b']
  * new.target

* Unary 单目运算符
  * delete a.b
  * void foo() 把其后的内容变成undefined
  * typeof a
  * \+ a
  * \- a
  * ~ a
  * ! a
  * await a  
  
```javascript
for(var i=0;i<10;i++){
  var button = document.createElement("button");
  document.body.appendChild(button);
  button.innerHTML = i;
  void function(i){
  button.onclick = function(){
     console.log(i);
    }
  }(i)
}
//void 和(function(i){})(i)是等效的
```
* Exponental
  * ** 右结合
    * 3\*\*2\*\*3 --> 3**(2**3)

* 逻辑运算符
 * a||b `若a为真，则执行a，否则执行b`
 * a && b `若a为false，则执行a，否则执行b`  
 > 逻辑运算符不转换，只有!!转换。
* 三目运算符  

* 装箱
 * 构造器 String、Number、Boolean、Symbol
   * String(1) --> '1', Object(a)和new Object(a)是等同的，都会生成一个对象。  

Symbol不可以用`new`,可以用symbol构造器进行装箱，Symbol(1);可以用Object对Symbol进行装箱，如Object(symbol(1))   
* 拆箱  
`1 + {valueOf(){return 2},toString(){return 2},[Symbol.toPrimitive](){turn 3}} //4,[Symbol.toPrimitive]优先级最高，其次是valueOf`   

`arguments.length`: 函数传入实参的数量

* BlockStatement
  * 语句内遇到非Normal类型的语句后面的语句就不再执行。
* Iteration
```javascript
//for循环中块级作用域和（）的部分是两个不同的作用域。
for(let i=0; i<10; i++>){
  let i = 0;
  console.log(i)
}
```
能够迭代的对象都可以用for of来循环
for of => Iterator => Generator/Array