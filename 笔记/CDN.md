# ES6 变量定义
> 大早上被扫盲了，记录一下一个小时知道的只是点。
##  var cost let
   ### 原来只是知道var 定义变量，可以变量声明提前；let 是定义变量，但是不会有变量声明变量提前是块级作用域，const 定义常量；
   * 使用var 声明变量，其作用域为该语句所在的函数内，且存在变量提升的现象；
   * 使用let 声明变量，作用域为该语句的代码块内，不存在变量提升；不能声明已经存在的变量
   * 使用const 声明变量的常量，在后面的代码中是不可以修改该常量的值；

   > const 不能修改的是栈 内存的值和地址。
   * 基本类型 Boolen Number String 是直接把值存在栈内；
   * 引用类型 Object 是把值存放在对应的地址中；
   ```
    const a = new String('123') ;
    a = '456'； 
    也是不允许的，因为 a = '456' 内部原理有地址改变: 
    temp = new String('456')
    a = temp
    销毁 temp

   ```
# CDN 
## 这个就是 我被扫盲的点，原来只是知道 CDN存放静态资源，但是为啥这样，有什么好处，具体又是个什么东东，我不知道！！！

## CDN 是神马？

### 这是官方的说发： 全称:Content Delivery Network或Content Ddistribute Network，即内容分发网络

## 为啥要用CDN？ 有什么目的？
 * 现在网络的时代，这个大家都知道。本人感觉离开网络不能生活。那么中国这么多人口，肯定网络拥挤啊。有什么方法解决或者减缓这个现状；
 *  所以 解决Internet网络拥挤的，提高用户的访问的速度，说了变天就是Cdn 就像外卖小哥一样，把你想要的信息送到你手里。CDN的意图就是尽可能的减少资源在转发、传输、链路抖动等情况下顺利保障信息的连贯性。
 * 通俗一点 就是，静态资源上传到服务器上，然后分发给很多服务器，你访问的话，会根据你的位置，就近给你派发信息；其实就是 我们淘宝网购，我们下单这家店铺有很多分店，会根据你的收货地址调最近的货给你发。这样你就很快能收到货了。

 ## 是如何实现的CDN 网络的？


* 当用户点击网站页面上的内容URL，经过本地DNS系统解析，DNS系统会最终将域名的解析权交给CNAME指向的CDN专用DNS服务器。CDN的DNS服务器将CDN的全局负载均衡设备IP地址返回用户。用户向CDN的全局负载均衡设备发起内容URL访问请求。
* CDN全局负载均衡设备根据用户IP地址，以及用户请求的内容URL，选择一台用户所属区域的区域负载均衡设备，告诉用户向这台设备发起请求。
* 区域负载均衡设备会为用户选择一台合适的缓存服务器提供服务，选择的依据包括：根据用户IP地址，判断哪一台服务器距用户最近；根据用户所请求的URL中携带的内容名称，判断哪一台服务器上有用户所需内容；查询各个服务器当前的负载情况，判断哪一台服务器尚有服务能力。基于以上这些条件的综合分析之后，区域负载均衡设备会向全局负载均衡设备返回一台缓存服务器的IP地址。
* 全局负载均衡设备把服务器的IP地址返回给用户。用户向缓存服务器发起请求，缓存服务器响应用户请求，将用户所需内容传送到用户终端。如果这台缓存服务器上并没有用户想要的内容，而区域均衡设备依然将它分配给了用户，那么这台服务器就要向它的上一级缓存服务器请求内容，直至追溯到网站的源服务器将内容拉到本地。

## CDN 对前端优化
 * 如果前端 请求图片的时候 会携带cookie 这样每次请求 都会携带cookie 如果静态资源 放在DN 上，不会携带cookie  减少HTTP 请求的字节；

 ### [CDN 参考](https://www.zhihu.com/question/37353035)




