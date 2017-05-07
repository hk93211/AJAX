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
* 4.1. readyState:返回当前XMLHttp请求的状态,有五种状态:    　 
```
　　状态: 0 : 请求未初始化    　　
　　状态: 1 : 请求已经建立    　　
　　状态: 2 : 请求已经发送    　 　　
　　状态: 3 : 请求处理中    　 　　
　　状态: 4 : 请求已经完成      　　　
```
* 4.2. onreadystatechange:readyState状态改变的事件触发器,用来指定当readyState发生变化时处理事件     
* 4.3. responseText：将响应信息以字符串的形式返回。     
* 4.4. responseXML：将响应信息格式化为XML文档的形式返回。    
* 4.5. status：当前Http请求的状态，下面列几个重要的，经常用到的状态。  
```
状态值: 200 : 交易成功
状态值: 404 : 没有发现文件,查询或URI
状态值: 500 : 服务器产生内部错误
```

## 5.XMLHttpRequest的方法
  * 5.1. open(method,url,asynch,username,password)方法将创建一个新的Http请求。
  ```
        method（请求方法）：GET,POST和PUT(一般不用)
        url：请求的地址
        asynch：可选参数，用来指定此请求是同步还是异步方式，默认为trun(异步)
        username,password：可选参数，服务器需要验证时用的，一般不用
  ```
  
  * 5.2.send(content)方法用来向服务器发送具体的请求,content仅用于post。
  
## 6.GET 还是 POST
  与POST相比,GET更简单也更快，并且在大部分情况下都能用,然而,在以下情况中,请使用 POST 请求:   
 ```
    无法使用缓存文(更新服务器上的文件或数据库)    
    向服务器发送大量数据(POST 没有数据量限制)    
    发送包含未知字符的用户输入时，POST 比 GET 更稳定也更可靠    
 ```
  
## 7.jQuery发送网络请求
ajax方法
```
  $.ajax({
                "url":"02-jQuery-network.php",
                "data":"username=zhangsan&password=123456",
                "success":function (data) {
                    console.log("成功" + data);
                },
                "error":function (dataCode) {
                    console.log("失败" + dataCode);
                },
                "type":"POST"
            }
        )
  ```
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
