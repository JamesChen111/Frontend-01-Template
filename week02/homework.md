# 写一个正则表达式匹配所有Numer直接量
* 整数
`/^-?[0-9]+$/g`
* 浮点数
`/^[-+]?[0-9]*\.?[0-9]+$/g`
* 二进制数
`/^[0-1]+$/g`
* 八进制
`/^0[oO][0-7]+$/g`
* 十六进制
`/^0[xX]([a-fA-F0-9])\1*$/g`
# 写一个UTF-8 Encoding的函数
```javascript
function UTF8_encoding(str){
    let utf_8 = '',fill_0,utf_8_len;
    const code16 = '0x'+str.codePointAt().toString(16);
    const code2 = str.codePointAt().toString(2);
    const len = code2.length;
    if(code16 >= 0 && code16 <= 0x7F){
      utf_8 = '0' + code2;
    } else if(code16 >= 0x80 && code16 <= 0x7ff){
      if(len < 11){
        fill_0 = 11 - len,utf_8 = '110';

        for(let i=0; i<fill_0; i++){
          utf_8 += '0'
        };
        utf_8_len = utf_8.length;
        utf_8 = utf_8 + code2.slice(0,8-utf_8_len) + '10' + code2.slice(8-utf_8_len)  
      } else {
        utf_8 += '110'+ code2.slice(0, 6) + '10' + code2.slice(11)
      }
    } else if (code16 >= 0x800 && code16 <= 0xFFFF){
      if(len < 16 && len > 12){
        fill_0 = 16 - len,utf_8 = '1110';
        for(let i=0; i<fill_0; i++){
          utf_8 += '0'
        };
        utf_8_len = utf_8.length;

        utf_8 += code2.slice(0,8-utf_8_len) + '10' + code2.slice(8-utf_8_len,14-utf_8_len)+'10'+code2.slice(14-utf_8_len)
      } else {
        utf_8 = '1110000010'+ code2.slice(0,6) + '10' + code2.slice(6)
      }
    } else if(code16>=0x10000 && code16 <= 0x10FFFF){
        if(len > 18 && len <= 21) {
          fill_0 = 21 - len,utf_8= '11110';
          for(let i=0;i<fill_0;i++){
            utf_8 += '0'
          };
          utf_8_len = utf_8.length
          utf_8 += code2.slice(0,8-utf_8_len)+'10'+code2.slice(8-utf_8_len,14-utf_8_len)+'10'+code2.slice(14-utf_8_len,20-utf_8_len)+'10'+code2.slice(20-utf_8_len)
        } else {
          fill_0 = 18 - len,utf_8 = '1111000010';
          for(let i=0;i<fill_0;i++){
            utf_8_len += '0'
          };
          utf_8_len = utf_8.length;
          utf_8 += code2.slice(0,8-utf_8_len)+'10'+code2.slice(8-utf_8_len,14-utf_8_len)+'10'+code2.slice(14-utf_8_len)
        }
    } else {
      utf_8 = '超出编码范围'
    }
    return utf_8
  }
```
# 写一个正则表达式，匹配所有的字符串直接量
`/[\u0021-\u007E]{6,16}|[\x21-\x7E]{6,16}|(['"])(?:(?!\1).)*?\1/g`