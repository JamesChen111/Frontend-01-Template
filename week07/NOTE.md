# 每周总结可以写在这里
* toy brower
还在做。。。

* 获取css标准
```
var lis = document.getElementById("container").children;
var result = [];
for(let li of lis){
  if(li.getAttribute('data-tag').match(/css/))
      result.push({
        name:li.children[1].innerText,
        url: li.children[1].children[0].href
        })
}
```
* 获取css属性
```
var iframe = document.createElement("iframe");
  document.body.innerHTML = "";
  document.body.appendChild(iframe);

  function happen(element, event){
    return new Promise(function(resolve){
      let handler = () => {
        resolve();
        element.removeEventListener(event, handler)
      }
      element.addEventListener(event,handler)
    })
  }
  
  void async function(){
    for(let standard of standards){
      iframe.src = standard.url;
      await happen(iframe, "load");
    }
  }();
```