# 每周总结可以写在这里
## Animation
* animation-duration 动画时长
* animation-timing-function 动画的时间曲线
  * ease | ease-i | ease-out | ease-in-out
* animation-delay 动画开始前的延迟
* animation-iteration-count 动画的播放次数;
  *  infinite | <number>
* animation-direction 动画的方向  
  * normal | reverse | alternate(交替) | alternate-reverse
* animatiion-fill-mode 确定动画在执行前后两个阶段应用的样式
* animation-play-state 确定动画是否正在播放
* animation-name 动画名称
  * keyframes类型，需要配合@规则使用

## keyframes
> 定义了动画的关键帧。keyframes的主体结构是一个名称和花括号中的定义，它按照百分比来规定数值。

```
@keyframes mykf {
//这里0和100%可以替换成from to
    0 {top: 0;}
    50% {top: 30px;}
    100% {top: 30px}
}
```

## Transition
* transition-property 要变换的属性
* transition-duration 变换的时长
* transition=timing-function 时间曲线
* transition-delay 延迟  

# HTML
## HTML 的定义: XML 与 SGML
[DTD](https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd)  

XML 文件的文档类型定义（Document Type Definition）可以看成一个或者多个 XML 文件的模板，在这里可以定义 XML 文件中的元素、元素的属性、元素的排列方式、元素包含的内容等等。

DTD（Document Type Definition）概念缘于 SGML，每一份 SGML 文件，均应有相对应的 DTD。对 XML 文件而言，DTD 并非特别需要，well-formed XML 就不需要有 DTD。DTD 有四个组成如下:  
* 元素（Elements）
* 属性（Attribute）
* 实体（Entities）
* 注释（Comments）

### 常用实体
* " `&quot;`
* \> `&gt;`
* \< `&lt;`
* & `&amp;`  
### 合法元素
* Element
* Text文本
* Comment
* DocumentType<!Doctype html>
* ProcessingInstruction 处理信息(没用)
* CDATA  
## DOM API
### NODE
* Element元素型节点
* Document文档根节点
* Character字符数据 包括文本节点 注释 处理信息
* DocumentFragment文档片段 不会产生真实dom 可较少dom操作  
* DocumentType 文档类型节点  
### 导航类操作
* parentNode
* childNodes
* firstChild
* lastChild
* nextSibling
* previousSibling  
### 修改操作
* appendChild
* insertBefore
* removeChild
* replaceChild
### 高级操作
* compareDocumentPosition 用于比较两个节点关系的函数
* contains 检查一个节点是否包含另外一个节点
* isEqualNode 检查两个节点是否完全相同
* isSameNode 检查两个节点是否是同一个节点 实际可以在 JS 中用===去判断
* cloneNode 复制一个节点 如果参数为 true 会连同子元素做深拷贝