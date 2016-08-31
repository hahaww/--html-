最近一直在开发移动端的html页面 在安卓和IOS 兼容上遇到很多问题  现在总结一下我遇到的问题  以及我市怎么解决这些问题的

1、在IOS里 过长的一串  数字 它会自动给识别成手机号码  要是一不小心触碰到 就会打电话  这个就用一个标签就可以解决
<meta name="format-detection" content="telephone=no" />
<meta name="format-detection" content="email=no" />
<meta name="format-detection" content="address=no" />
<meta name="format-detection" content="date=no" />

2、input输入框  type=number 低版本的手机 或者有些IOS手机 浏览器  placeholder 失效
这个时候如果你只是想用来 输入数字的话  可以用 type= tel

还有些时候maxlength  失效   这个我是用js  控制的

3，IOS的绑定click  事件  失效

但它并不是全部都失效  有一些按钮绑定click  事件 就是可以的

有些Click  事件失效  只要把这个加上cursor：poiner  就可以

网上有人说用touch  事件 但是这个事件也不好使 他会有穿透

还有人说用e.preventDefault();  这个我也试过 没有起什么作用

4.position：fixed  失效 

当手机键盘弹出的时候  如果有弹框的话  弹框就会 弹来弹去 位置会变动

所以 看到有人事这样解决的  我试了一下 确实好使

弹框定位为position:absoulute

包含弹框的 加上这个

overflow-y: scroll;
-webkit-overflow-scrolling: touch;

例如：

<div class="mask">

　　<div class="alertBox"></div>

</div> 

<style>

.mask{overflow-y: scroll;
-webkit-overflow-scrolling: touch;}

.alertBox{position:absolute}

</style>
5.在移动端显示 input disabled 的时候 透明度会降低   
在css  里这样写
color: #000;-webkit-text-fill-color:#000;-webkit-opacity:1;opacity: 1;

6.在移动端 body  overflow-y:hidden 失效
代码如下
<body>
<p>我是一个p标签</p>
<p>我是一个p标签</p>
<p>我是一个p标签</p>
<p>我是一个p标签</p>
<p>我是一个p标签</p>
<div class="mask"></div>
</body>

body  里面有很多很多p标签  超过一屏  会出现滚动条
mask  是一个 遮罩  
.mask{position:fixed; width:100%; height:100%; background:rgba(34,34,34,0.6);  z-index:10; top:0;}

当遮罩出现的时候  不想让body滚动  

在web端  body overflow-y：hidden  就可以
但是在移动端  就不可以  再给body 加一个 position：fixed  就可以啦  
.overflow{overflow-y:hidden;position:fixed}

这样在手机上看 就不会滚动啦



上面写的这些问题 在大神看来可能有点小白  有一些在网上百度也是可以百度到的    但是对我来说是一个总结  也是一个认识吧  
