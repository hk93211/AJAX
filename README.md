# AJAX
## 1.Ajax 
　　Ajax(Asynchronous Javascrpt And Xml)是一种运用于浏览器的技术,它可以在浏览器与服务器之间使用异步通信机制进行数据通信，从而允许浏览器向服务器获取少量信息而不是刷新整个页面。Ajax并不是一种新的技术，或者说它不是一种技术，它只是多种技术的综合：JavaScript、Html、Css、Dom、Xml、XMLHttpRequest等技术按照一定的方式在协作中发挥各自的作用就构成了Ajax。
  
## 2.Ajax的通信步骤
    1.新建一个XMLHttpRequest对象  
    2.open方法表示初始化请求,此时没有发送  
    3.定义数据返回后的回调函数,里面的代码在readystatechange值改变的时候执行  
    4.发送请求
## 3.XMLHttpRequest
　　XMLHttpRequest是Ajax技术的一个核心，没有它Ajax无从运作,XMLHttpRequest是XMLHttp组件的一个对象，使用XMLHttpRequest可以实现浏览器端与服务器端进行异步通信。通过HttpRequest对象，Web应用程序无需刷新页面就可以向服务器提交信息，然后得到服务器端的返回信息。
  
## 4.如何使用XMLHttpRequest对象
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

## 5.XMLHttpRequest属性介绍
* 4.1. readyState:返回当前XMLHttp请求的状态(只能读不能写),有且只有五种状态:    　 
```
　　状态: 0 : 请求未初始化    　　
　　状态: 1 : 请求已经建立    　　
　　状态: 2 : 请求已经发送    　 　　
　　状态: 3 : 请求处理中,服务器已经返回了数据(但是还没有被解析,可能只是一段http报文)    　 　　
　　状态: 4 : 请求已经完成,数据解析已经完成      　　　
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

## 6.XMLHttpRequest的方法
  * 5.1. open(method,url,asynch,username,password)方法将创建一个新的Http请求。
  ```
        method（请求方法）：GET,POST和PUT(一般不用)
        url：请求的地址
        asynch：可选参数，用来指定此请求是同步还是异步方式，默认为trun(异步)
        username,password：可选参数，服务器需要验证时用的，一般不用
  ```
  
  * 5.2.send(content)方法用来向服务器发送具体的请求,content仅用于post。
  
## 7.get请求
* 将表单数据以名称/值对的形式附加到URL中
* URL的长度是有限的(大约3000个字符)
* 绝对不要使用GET来发送敏感数据!(因为在URL中是可见的)
* 对于用户希望加入书签的表单提交很有用
* GET更适用于非安全数据,比如在Google中查询字符串,通过get的方式请求数据,那么对于sent()方法,参数为null就可以  
**get请求中如果有中文,可能会报错**, 所以我们一般会对参数重新编码  
      var url="open.php?username="+encodeURI(username)+"&password="+password;

## 8.post请求
* 将表单数据附加到HTTP请求的body内(数据不显示在URL中)
* 没有长度限制
* 通过 POST 提交的表单不能加入书签  
post请求传输数据的时候，数据是作为send方法的参数传输的。
```
var param = 'username='+username+'&password='+password;
xhr.send(param);
```
一般数据接收方，也就是后台对于post请求，会默认其数据类型是表单数据类型，所以需要我们设置一下post请求的数据格式，否则我们提交的数据会因为编码格式不对，导致后台取不到我们提交的数据。

    xhr.setRequestHeader("Content-Type","application/x-www-form-urlencoded; charset=gb2312");

## 9.url中的参数传递格式
    url是一个地址,当我们需要传递参数的时候,首先需要在url后添加一个?号,然后后米娜跟上我们的参数,比如username="哈士奇",参数之间要用&号连接。比如username="哈士奇"&ppassword="我爱萨摩耶"。完整的例子如下：http://www.whutyzy.cc/index.php?username=哈士奇&ppassword=我爱萨摩耶

## 10.GET 还是 POST
  与POST相比,GET更简单也更快，并且在大部分情况下都能用,然而,在以下情况中,请使用 POST 请求:   
 ```
    无法使用缓存文(更新服务器上的文件或数据库)    
    向服务器发送大量数据(POST 没有数据量限制)    
    发送包含未知字符的用户输入时，POST 比 GET 更稳定也更可靠    
 ```
  
## 11.jQuery发送网络请求
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
  
## 12.jsonp
　　　在讲jsonp是什么之前,我们首先看下这么一个情况,我们想写一个天气预报的实时页面,数据肯定是从其他网站来的,比如url:"http://tq.360.cn/api/weatherquery/querys?app=tq360&code=$code&_jsonp=renderData&_=1429595284544"  
   这个接口就提供了我们需要的天气数据,所以我们只需要使用ajax发送请求到这个网站上,再接收天气数据在页面上渲染就可以了,但是当我们写好代码运行的时候会报错,提示No 'Access-Control-Allow-Origin' header is present on the requested resource. Origin 'http://localhost:63342' is therefore not allowed access..大概意思是无法接收请求,原因是发生了跨域,也就是我们访问了其他域名,处于安全原因,我们不会接收其他域名发送过来的文件数据,对于这个跨域的问题,有不同的解决方案,我们使用的方案是jsonp
    jsonp到底是什么？不要着急，继续往下看。
    虽然浏览器不让我们接收其他网站的数据，但是允许我们加载其他网站上的script文件。比如比较常见的引入jquery：  
```<script src="https://cdn.bootcss.com/jquery/3.2.1/jquery.js"></script>```
    所以我们完全可以通过script的方式来加载数据。
```
<body>
<script src="https://cdn.bootcss.com/我爱哈士奇.php"></script>
</body>
```
　　　这一段绕来绕去做了个什么？其实就是将传回来的数据放到之前定义好的函数中执行。因为后台的获取这个函数名是根据url传过来的参数取出来的，所以这个参数名jsonp最好统一，方便后台程序员编写接口。
到这里，我们再看下jsonp的定义与背景：  
* 一个众所周知的问题，Ajax直接请求普通文件存在跨域无权限访问的问题，甭管你是静态页面、动态网页、web服务、WCF，只要是跨域请求，一律不准；　　
* 不过我们又发现，Web页面上调用js文件时则不受是否跨域的影响（不仅如此，我们还发现凡是拥有”src”这个属性的标签都拥有跨域的能力，比如<script>、<img>、<iframe>；  　　
* 于是可以判断，当前阶段如果想通过纯web端（ActiveX控件、服务端代理、属于未来的HTML5之Websocket等方式不算）跨域访问数据就只有一种可能，那就是在远程服务器上设法把数据装进js格式的文件里，供客户端调用和进一步处理； 　　 
* 恰巧我们已经知道有一种叫做JSON的纯字符数据格式可以简洁的描述复杂数据，更妙的是JSON还被js原生支持，所以在客户端几乎可以随心所欲的处理这种格式的数据；  　　
* 这样子解决方案就呼之欲出了，web客户端通过与调用脚本一模一样的方式，来调用跨域服务器上动态生成的js格式文件（一般以JSON为后缀），显而易见，服务器之所以要动态生成JSON文件，目的就在于把客户端需要的数据装入进去。  　　
* 客户端在对JSON文件调用成功之后，也就获得了自己所需的数据，剩下的就是按照自己需求进行处理和展现了，这种获取远程数据的方式看起来非常像AJAX，但其实并不一样。    
* 为了便于客户端使用数据，逐渐形成了一种非正式传输协议，人们把它称作JSONP，该协议的一个要点就是允许用户传递一个callback参数给服务端，然后服务端返回数据时会将这个callback参数作为函数名来包裹住JSON数据，这样客户端就可以随意定制自己的函数来自动处理返回数据了。    
   

  当然，jquery中也提供了封装好的jsonp方法。最后再提一句，一般不会选择在页面上直接引入<script>这种方式，而是在js中动态生成<script>节点。
  
  
  
  
  
  
  
  
