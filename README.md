# AJAX
## 1.Ajax 
　　Ajax(Asynchronous Javascrpt And Xml)是一种运用于浏览器的技术,它可以在浏览器与服务器之间使用异步通信机制进行数据通信，从而允许浏览器向服务器获取少量信息而不是刷新整个页面。Ajax并不是一种新的技术，或者说它不是一种技术，它只是多种技术的综合：JavaScript、Html、Css、Dom、Xml、XMLHttpRequest等技术按照一定的方式在协作中发挥各自的作用就构成了Ajax。
  
## 2.XMLHttpRequest
　　XMLHttpRequest是Ajax技术的一个核心，没有它Ajax无从运作,XMLHttpRequest是XMLHttp组件的一个对象，使用XMLHttpRequest可以实现浏览器端与服务器端进行异步通信。通过HttpRequest对象，Web应用程序无需刷新页面就可以向服务器提交信息，然后得到服务器端的返回信息。
  
## 3.如何使用XMLHttpRequest对象
　　使用XMLHttpRequest首先要创建一个XMLHttpRequest对象,请看一下例子
```javascript
<script type="text/javascript">
function createXmlHttp(){
        if(window.ActiveXObject){
                xmlHttp=new ActiveXObject("Microsoft.XMLHTTP");
                //alert("IE XmlHttp");
        }
        else if(window.XMLHttpRequest){
                xmlHttp=new XMLHttpRequest();
                //alert("Other XmlHttp");
        }
}
</script>
```
这是一个兼容三大浏览器的创建XMLHttpRequest方法

## 4.XMLHttpRequest属性介绍
