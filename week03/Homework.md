* String转换成Number
```javascript
function StringToNumber(str, x=10){
    let chars = str.split('');
    let number = 0;
    var i = 0;
    while(i<chars.length && chars[i] !== '.'){
      number = number * x;
      number += chars[i].codePointAt(0) - '0'.codePointAt(0);
      i++;
    }
    if(chars[i] === '.') i++;
    let fraction = 1;
    while(i < chars.length){
      fraction = fraction /10;
      number += (chars[i].codePointAt(0) - '0'.codePointAt(0))*fraction;
      i++
    }
    return number
  }
```
* Number转换成String
```javascript
function NumberToString (num, x=10) {
  let isPositive = num>0 ? '':'-'; // 判断num是不是正数
  let result = '';
  num=Math.abs(num);
  let integer = Math.floor(num);
  //获取小数部分
  let fraction = String(num).match(/\.\d+$/);
  if (fraction) fraction = fraction[0];

  while (integer > 0) {
    result = integer % x + result;
    integer = Math.floor(integer / x);
  }
  return fraction ? `${isPositive}${result?result:0}${fraction}` : `${isPositive}${result}`;
}
```