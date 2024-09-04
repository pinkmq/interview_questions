### 1. HTML
#### 1.1 简述一下http和https
- http是超文本传输协议，信息是明文传输，https加了SSL协议，可进行加密传输、身份认证，比http协议更安全
- http和https使用的是完全不同的连接方式，用的端口也不一样，前者是80，后者是443
- https协议需要ca申请证书，一般免费证书较少，因而需要一定费用

#### 1.2 HTML5增加了哪些属性和标签，还有哪些api
- 新增语义化标签：header、footer、nav、article、section、asicde
- 新增表单属性：min、max、step、placeholder、autofocus、required、pattern、multiple
- 新增数据存储localstorage sessionstorage
- 新增音频视频
- 新增画布canvas

#### 1.3 对HTML语义化标签的理解
- 用合适的标签和属性组合文档结构，增强代码可读性
- css不能正常加载时，仍然能够保证基本的文档结构
- 有利于后期维护
- 有利于团队合作
- 有利于SEO
- 有利于用户体验

#### 1.4 常见布局方式
- 固定布局、响应式布局、弹性布局、自适应布局、流式布局

#### 1.5 两边固定中间自适应怎么实现
- flex布局：使用display: flex，左右两栏设置固定宽度，中间栏设置flex: 1，让它自动填充剩余空间
- 自身浮动法：左栏左浮动，右栏右浮动，中间栏放在最后，不设置浮动属性，它会自动填充剩余空间
- 绝对定位法：左右栏使用position: absolute固定在页面两侧，中间栏通过设置margin-left和margin-right来自适应布局
- margin负值法：两边固定宽度的元素使用float浮动，中间元素设置width: 100%，通过左右栏的负margin值让中间元素自适应剩余空间

#### 1.6 页面导入样式时，使用link和@import有什么区别
- link标签用在html中，支持并行加载，性能更好；@import用于在CSS中，加载可能会延迟

#### 1.7 title与h1的区别，b与strong的区别，i与em的区别
- title定义了网页标题，显示在浏览器标签上，h1表示页面的主要标题，显示在网页内容上。对于SEO来说，title比h1更重要
- b和strong都用来加粗文本，strong表示标签内字符比较重要，用以强调
- i和em都用来倾斜文本，em表示标签内字符比较重要，用以强调

#### 1.8 img标签的title和alt有什么区别
- title：鼠标移入到图片显示的值
- alt：图片无法加载时显示的值。为了增加SEO效果，要加入alt属性来描述图片内容或关键词

#### 1.9 href和src的区别
- href不会直接下载资源，而是创建一个通道，当用户点击链接时，浏览器会导航到指定的URL
- src浏览器会下载资源并将其嵌入到当前文档中，替代当前元素


### 2. CSS
#### 2.1 盒子模型
- 标准盒子模型：margin、border、padding、content `box-sizing: content-box;`
- IE盒子模型：margin、content( border + padding + content ) `box-sizing: border-box;`

#### 2.2 重绘和重排(回流)
- 重绘：对元素的样式进行修改，比如color和background-color，浏览器不需要重新计算几何属性，直接绘制该元素的新样式，那么就只触发了重绘。
- 重排：当一个元素自身的宽高、位置、显隐或元素内部的文字结构发生变化，导致需要重新构建页面，这个过程就是重排(也叫回流)。产生回流一定会造成重绘，但是重绘不一定会造成回流。

#### 2.3 CSS选择器优先级
- !important > 内联样式(行间样式) > id选择器 > 类选择器 > 标签选择器 > 通配( * )

#### 2.4 实现元素的垂直居中
- 定位 + transform  `position: absolute; left: 50%; top: 50%; transform: translate(-50%, -50%);`
- 定位 + margin `position: absolute; left: 0; right: 0; top: 0; bottom: 0; margin: auto;`
- flex布局  `display: flex; align-items: center; justify-content: center;`

#### 2.5 什么是BFC
- BFC也就是块格式化上下文，是一个独立的容器，容器里的子元素不会影响到外面的元素。
- 触发BFC：
  - float属性为left、right
  - position属性为absolute、fixed
  - display属性为inline-block、flex、grid、table-cell、table-caption
  - overflow属性为hidden、auto、scroll

#### 2.6 清除浮动有哪些方式(浮动塌陷)
- 元素浮动以后，脱离正常文档流，导致父元素无法被撑开(高度易陷)，且会影响后续正常布局。
- 清浮动方法：
  - 给浮动元素的父元素添加一个伪元素	`.clearfix::after { content: ''; clear: both; display: table; }`
  - 触发BFC
  - 给浮动标签的父标签固定高度(不够灵活)

#### 2.7 margin塌陷
- 在两个盒子嵌套的时候，父盒子和子盒子同时设置margin的时候会出现实际的magin取的是两个margin的最大值。
- 解决方法：
  - 给父元素添加一个伪元素	`.clearfix::after { content: ''; clear: both; display: table; }`
  - 触发BFC
  - 给父级设置边框或内边距

#### 2.8 隐藏元素的方法
- display: none;(不占位)	 visibility: hidden; (占位) 	opacity: 0; (占位)  position 移到外部，z-index 

### 6. 其他
#### 6.1 一个完整的http请求都发生了些什么事情？
```
你决定要去咖啡店：
想象你想去一家咖啡店（网站），你在手机上找到它的地址（网址）。

你去咖啡店：
你拿着地址，去到那家咖啡店（发出 HTTP 请求）。你告诉店员你想要一杯拿铁（请求某个网页或资源）。

咖啡店接待你：
店员（服务器）听到你的订单后，开始准备你的咖啡（处理请求），他们可能需要时间来完成你的订单。

咖啡店给你咖啡：
店员准备好你的咖啡后，给你一杯拿铁（HTTP 响应），上面可能还有个标签，告诉你这是拿铁（响应头），还有咖啡的热度和类型（状态码、内容类型等）。

你享用咖啡：
你拿到咖啡后，看看是不是你点的那种，满意的话就开始享用（浏览网页内容）。

你离开咖啡店：
一旦你喝完咖啡，你离开了咖啡店（关闭连接），这时店员也可以清理桌子，准备迎接下一个顾客。

总结
在这个过程中，你像是从浏览器发出一个请求（去咖啡店点单），服务器处理你的请求（咖啡店准备咖啡），然后把结果（咖啡）返回给你，最后你享受内容并离开（浏览器展示网页并关闭连接）。
```

#### 6.2 TCP三次握手和TCP四次挥手
```
三次握手（建立连接）
第一次握手：你（客户端）要和对方（服务器）打招呼，告诉对方你想要开始聊天。你发出一个“你好，我想连接”的信号。
第二次握手：对方（服务器）收到你的打招呼信号后，回应你一个“你好，我愿意聊天，但我们需要确认一下。” 它会发回一个包含两个信号的回应：一个是确认你的“你好”，另一个是它自己的“我也想聊”的信号。
第三次握手：你收到对方的回应后，再发一个确认信号，告诉对方“好的，我收到了你的回应，我们可以开始聊天了。”这样，双方都确认了连接可以建立了。

四次挥手（断开连接）
第一次挥手：你（客户端）决定不再聊天了，发出一个“我想断开连接”的信号。
第二次挥手：对方（服务器）收到你的断开信号后，回复一个“收到，我明白了。” 它发回一个确认的信号，但它自己可能还在处理一些事情，所以它会继续与你保持连接一段时间。
第三次挥手：对方（服务器）完成了所有的处理，准备好断开连接了，它发出一个“我也要断开了”的信号。
第四次挥手：你（客户端）收到对方的断开信号后，再发一个确认信号，告诉对方“好的，我已经收到了。” 这样，双方就完全断开了连接。
```
