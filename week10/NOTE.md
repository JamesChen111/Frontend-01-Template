# 每周总结可以写在这里
# Range API
* var range = new Range()
* range.setStart(element, 9)
* range.setEnd(element, 4)
* var range = document.getSelection().getRangeAt(0);
* range.setStartBefore
* range.setEndBefore
* rnage.setStartAfter
* range.selectNode
* range.selectNodeContents   

# CSSOM
## document.styleSheets
## Rules
* document.styleSheets[0].cssRules
* document.styleSheets[0].insertRule("p{color: pink}",0)
* document.styleSheets[0].removeRule(0)  

## getComputedStyle
* window.getComputedStyle(elt, pseudoElt)  
> 获取一个元素最终经过计算得到的属性

# window API
* window.open('url','_blank')

element.scrollTop *滑块顶部到滚动条顶部的距离*  
element.scrollHeight *滚动条的滚动区域*  
element.scrollBy(30,30) *使滚动条滚动的距离*  

## getClientRect()
document.getClientRects()*返回的是个数组，该数组包含元素里所有行盒的精确位置*   

## getBoundingClientRect()
返回某个元素的具体位置。配合transform实现拖拽

window.devicePixelRatio *设备像素比*