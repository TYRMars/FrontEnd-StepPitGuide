<h1 align="center">响应式网站开发📱</h1>
<p align="center"><img src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1496594903275&di=4e3edd5421a71e1369a30d5bc7f5cb2e&imgtype=0&src=http%3A%2F%2Fpmo804649.pic19.websiteonline.cn%2Fupload%2F1afw.jpg" /></p>
---

# 目录
#### 第一章 响应式简介
* [01-01](https://github.com/TYRMars/ResponseiveWeb#01-01) `响应式开发网站设计概念`
* [01-02](https://github.com/TYRMars/ResponseiveWeb#01-02) `响应式网站的优点与缺点`
* [01-03](https://github.com/TYRMars/ResponseiveWeb#01-03) `媒体查询`

* 更新中！
---

## 01-01
### 响应式开发网站设计概念


## 01-02
### 响应式网站的优点与缺点
#### 响应式的优点
* 减少工作量
    1. 网站、设计、代码、内容都只需要一份
    2. 多出来的工作量只是JS脚本、CSS样式做一些改动
* 节省时间
* 每个设备都能得到正确的设计
* 搜索优化
#### 响应式网站的缺点
* 会加载更多的样式和脚本资源
* 设计比较难精确定位和控制
* 老版本浏览器兼容不好

## 01-03
### 媒体查询
* CSS3

```CSS

@media all and (min-width:800px) and (orientation:landscape){
  /*...样式，应用于所有媒体类型*/
}

```
* `@media all`应用于所有的媒体类型，媒体类型可选择，可以是screen和print

* `and (min-width:800px) and (orientation:landscape)`逻辑查询操作符`not,and,only`连接

* `{}`如果为真则应用

* 也可以用`,`分割，和`or`是一个意思

* `not`代表非

```CSS
@media not all and (monochrome) {,,,}
/*等价于||*/
@media not (all and (monochrome)) {,,,}
```

```CSS
@media not screen and (color),print and (color) {}
/*等价于||*/
@media not screen and (color) or print and (color) {}
/*等价于||*/
@media (not (screen and (color))),print and (color) {}
```

* only:仅仅只有，防止老旧的浏览器，不支持带媒体属性的查询，而应用到给定的样式

```JavaScript
media = "only screen and (min-width:401px) and (max-width:600px)"
//旧浏览器解析：media="only"
media = "screen and (min-width:401px) and (max-width:600px)"
//旧浏览器解析：media="screen"
```

* only最好不要省略

#### CSS媒体属性简介

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

#### 视口viewport
* width:视口宽度（主窗口区域）PC原有的概念
* device-width:设备屏幕的宽度
* 手机上的视口问题
    * 布局视口（layout viewport）
    * 可视视口（visal viewport）
    * 理想视口（ideal viewport）

---

## 小技巧
* 图片
    * 必不可少的图片使用<img>引入
    * 可有可无的装饰性图片可以用标签的style引入
