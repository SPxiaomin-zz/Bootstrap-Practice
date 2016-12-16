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

- col-xs-*

    xs即extra small，是为手机准备的网格类，也就是在窗口 `< 768px` 的时候应用的样式。

- col-sm-*

    sm即small，用在小尺寸屏幕上，比如说平板电脑，在窗口 `>= 768px` 的时候应用的样式。

- 
