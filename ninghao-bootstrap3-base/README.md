# ninghao-Bootstrap3 基础课程学习笔记

## 导航

- [准备](#准备)

## 准备

### 下载Bootstrap

1. 先到 <http://getbootstrap.com/getting-started/> 下载最新版本的 bootstrap；
2. 再到 <http://jquery.com/download/> 下载 bootstrap 依赖的 jquery；

### 准备 HTML 文档

```html
<!DOCTYPE html>
<html lang="zh-hans">
<!-- hans: 简体中文，hant: 繁体中文 -->
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <!-- ie=edge: 告诉IE用最新的引擎渲染页面 -->

    <title>Bootstrap 3</title>

    <link rel="stylesheet" href="lib/bootstrap/css/bootstrap.min.css">
    <link rel="stylesheet" href="css/style.css">
</head>
<body>

    <script src="lib/jquery-3.1.1.min.js"></script>
    <script src="lib/bootstrap/js/bootstrap.min.js"></script>
</body>
</html>
```

## 布局

### 使用网格系统-Grid-system

<!-- TODO: 画出线状图出来理解、查一下有什么线状图工具 -->

`*` 代表的是占用的网格数量，Bootstrap 中一行的网格数量是 12 个。

Bootstrap 是移动设备优先的，因此在设置 `col-xs-*` 的样式的时候是没有使用媒体查询的，而是直接写样式的，其它的都是通过设置相应宽度的媒体查询实现 `@media (min-width: *) {}`。

- col-xs-*

    xs即extra small，是为手机准备的网格类，也就是在视口 `< 768px` 的时候应用的样式。

- col-sm-*

    sm即small，用在小尺寸屏幕上，比如说平板电脑，在视口 `>= 768px` 的时候应用的样式。

- col-md-*

    md即middle，用在中等设备上，在视口 `>= 992px` 的时候应用的样式。

- col-lg-*

    lg即large，用在大尺寸设备上，在视口 `>= 1200` 的时候应用的样式。

### 让页面居中显示的容器－.container

通过为元素多添加一个带有 `class="container"` 的父元素，就可以实现让页面居中显示。

`.container` 的具体样式规则如下:

```css
.container {
    padding-left: 15px;
    padding-right: 15px;
    margin-left: auto;
    margin-right: auto;
}

@media (min-width: 768px) {
    .container {
        width: 750px;
    }
}

@media (min-width: 992px) {
    .container {
        width: 970px;
    }
}

@media (min-width: 1200px) {
    .container {
        width: 1170px;
    }
}
```

从上面的样式就可以看出来，是通过 `css` 样式层叠特性 & `media` 来实现在不同屏幕尺寸上使用不同的宽度。

上面的样式规则中，先针对移动设备设置默认的样式规则，然后再通过使用媒体查询来根据屏幕不断增大的情况来设置样式，可以看出来采用了移动设备优先的思想。

### 网格类 & 混合使用网格类

网格类Bootstrap样式规则源码

使用一个类——`.col-xs-6`

```css
.col-xs-6 {
    width: 50%;
}

.col-xs-6 {
    float: left;
}
```

混合使用网格类Bootstrap样式规则源码

使用类——`.col-xs-6.col-sm-8`

```css
.col-xs-6 {
    width: 50%;
}

.col-xs-6 {
    float: left;
}

.col-sm-8 {
    width: 66.66666667%;
}

.col-sm-8 {
    float: left;
}
```

其实混合使用网格类布局的核心原则是——权重相同的样式规则，位置越靠后的覆盖位置靠前的。

### 内容列的顺序－push与pull

在不改变代码结构的情况下，改变元素的左右显示位置。使用这个样式的目的是便于SEO搜索优化。

`push` 是向右推，`pull` 是向左拉。

Bootstrap 使用的是以下方式实现效果 `position: relative;` & push `left: *%` & pull `right: *%`

### 嵌套的布局-nesting

嵌套布局简单来说，就是在 `.col-*-*` 中嵌套 `.col-*-*`，但是要注意将嵌套的 `.col-*-*` 包裹一层 `.row`。

<!-- TODO: 插入本子上的图——有无row，可以考虑用工具画 -->

但是容易造成如下的现象——

<!-- TODO: 插入图片 -->
产生了混排的现象。

解决方案有两种——

1. 分别放在单独的一个 `row`;
2. 增加一个无语义的 `div.clearfix`，来修复元素的浮动问题。

### 偏移的空间-offset

<!-- TODO: 正则表达式1-12的符号怎么表示 -->

使用 `.col-(xs|sm|md|lg)-offset-[1-12]` 对元素进行水平方向的偏移。

Bootstrap 实现的方式是借助 `margin-left` 进行偏移的，这里其实是借助了 `margin` 的百分比值是相对于宽度计算的特性。
