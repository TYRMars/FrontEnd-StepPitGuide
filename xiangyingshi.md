# 响应式开发

响应式网站开发📱

**目录**

**第一章 响应式简介**

* [01-01](https://github.com/TYRMars/ResponseiveWeb#01-01) `响应式开发网站设计概念`
* [01-02](https://github.com/TYRMars/ResponseiveWeb#01-02) `响应式网站的优点与缺点`
* [01-03](https://github.com/TYRMars/ResponseiveWeb#01-03) `媒体查询`
* [01-04](https://github.com/TYRMars/ResponseiveWeb#01-04) `px,em,rem`

**01-01**

**响应式开发网站设计概念**

* progressive enhancement 渐进增强
* graceful degradation 优雅降级 +
* 不管设备大小，应该包含相同的内容
* 根据设备大小不同，显示不同内容

```css
/*-------- iphone 4 and 4s ---------*/
/* Portranit and landscape */
@media only screen
and (min-device-width:320px)
and (max-device-width:480px)
and(-webkit-min-device-pixel-ratio:2){

}
/*-------- iphone 5 and 5s ---------*/
/* Portranit and landscape */
@media only screen
and (min-device-width:320px)
and (max-device-width:568px)
and(-webkit-min-device-pixel-ratio:2){

}
```

* 0-480 小屏幕
* 481-800 中屏幕
* 801-1400 大屏幕
* 1400+ 超大型屏幕

**01-02**

**响应式网站的优点与缺点**

**响应式的优点**

* 减少工作量
  1. 网站、设计、代码、内容都只需要一份
  2. 多出来的工作量只是JS脚本、CSS样式做一些改动
* 节省时间
* 每个设备都能得到正确的设计
* 搜索优化

  **响应式网站的缺点**

* 会加载更多的样式和脚本资源
* 设计比较难精确定位和控制
* 老版本浏览器兼容不好

**01-03**

**媒体查询**

* CSS3

```css
@media all and (min-width:800px) and (orientation:landscape){
  /*...样式，应用于所有媒体类型*/
}
```

* `@media all`应用于所有的媒体类型，媒体类型可选择，可以是screen和print
* `and (min-width:800px) and (orientation:landscape)`逻辑查询操作符`not,and,only`连接
* `{}`如果为真则应用
* 也可以用`,`分割，和`or`是一个意思
* `not`代表非

```css
@media not all and (monochrome) {,,,}
/*等价于||*/
@media not (all and (monochrome)) {,,,}
```

```css
@media not screen and (color),print and (color) {}
/*等价于||*/
@media not screen and (color) or print and (color) {}
/*等价于||*/
@media (not (screen and (color))),print and (color) {}
```

* only:仅仅只有，防止老旧的浏览器，不支持带媒体属性的查询，而应用到给定的样式

```javascript
media = "only screen and (min-width:401px) and (max-width:600px)"
//旧浏览器解析：media="only"
media = "screen and (min-width:401px) and (max-width:600px)"
//旧浏览器解析：media="screen"
```

* only最好不要省略

**CSS媒体属性简介**

* width:视口宽度
* height:视口高度
* device-width:渲染表面的宽度，就是设备屏幕的宽度。
* device-height:渲染表面的高度，就是设备屏幕的高度。
* orientation:检查设备处于横向还是纵向
* aspect-ratio:基于视口宽度和高度的宽高比。width/height 如：16/9,4/3
* device-aspect-ratio:渲染表面的宽度，就是设备屏幕的宽度
* color:每种颜色的位数bits 如：min-color：16位、9位
* resolution:检测屏幕或打印机的分辨率如：min-resolution:300dpi

`以上属性都可以添加min-或max-前缀`

**视口viewport**

* width:视口宽度（主窗口区域）PC原有的概念
* device-width:设备屏幕的宽度
* 手机上的视口问题
  * 布局视口（layout viewport）
  * 可视视口（visal viewport）
  * 理想视口（ideal viewport）

```markup
<meta name="viewport" content="width=device-width"></meta>
```

* 如果不写以上这句话布局视口的宽度是厂商的默认值
* 设置以上这句话以后布局视口将成为理想视口

```markup
<meta name="viewport" content="width=device-width,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no"/>
```

* minimum-scale 最小缩放比例 maximum-scale 最大缩放比例 user-scalable 禁用了用户缩放

**01-04**

**px,em,rem**

**px**

* 1px等于1个像素

  **em**

* em 相对单位长度
  1. em相对于参照物为父元素的font-size
  2. em具有继承的特点
  3. 当没有设置font-size时，浏览器会有一个默认的em设置：1em = 16px

     **rem**
* rem的相对参照物为根元素html,相对于参照物固定不变所以比较好计算
* 当没有设置font-size时，浏览器会有一个默认的rem设置：1rem=16px,这点与em是一致的
* 样式实现
  * font-size:62.5% 1rem = 10px \(10/16\*100%\)
  * font-size:100% 1rem = 16px

**小技巧**

**图片**

* 必不可少的图片使用引入
* 可有可无的装饰性图片可以用标签的style引入

**如何避免出发repaint/reflow**

* Display,的值会影响布局，从而影响整个页面元素的位置变化，所以会更改render树的结构
* 先将元素从document中删除，完成修改后再把元素放回原来的位置
* 如果需要创建多个DOM节点，可以使用DocumentFragment创建完成后一次性的加入document

  ```javascript
  //Create the fragment
  var fragment = document.createDocumentFragment();
  //add Dom to fragment
  var spanNode = document.createElement("div");
  for(var i = 0; i<10 ; i++){
  (function (i) {
    spanNode
  })(i)
  }
  ```

