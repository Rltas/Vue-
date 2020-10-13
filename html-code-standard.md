# html代码风格

## 缩进
* 使用 `2` 个空格做为一个缩进层级。

  ```html
<ul>
    <li>first</li>
    <li>second</li>
</ul>
```

## 换行
* 每行尽量不超过 `80` 个字符。(过长的代码不容易阅读与维护)

## 命名
* `class` 单词全字母小写，单词间以 `-` 分隔，一个标签尽量不要超过4个类名。
* `class` 代表相应模块或部件的内容或功能，不以样式信息进行命名。

```html
<!-- good -->
<div class="sidebar"></div>
<!-- bad -->
<div class="left"></div>
```

* 元素 `id` 必须保证页面唯一。(同一个页面中，不同的元素包含相同的 `id`，不符合 `id` 的属性含义。
  并且使用 `document.getElementById` 时可能导致难以追查的问题。)
* `id` 建议单词全字母小写，单词间以 `-` 分隔。同项目保持风格一致。
* 同一页面，应避免使用相同的 `name` 与 `id`。(IE 浏览器会混淆元素的 `id` 和 `name` 属性， `document.getElementById` 可能获得不期望的元素)

```html
<input name="foo">
<div id="foo"></div>
<script>
// IE6 将显示 INPUT
alert(document.getElementById('foo').tagName);
</script>
```

## 标签
* 标签名必须使用小写字母。
* 对于无需自闭合的标签，不允许自闭合。(常见无需自闭合标签有 `input`、`br`、`img`、`hr` 等。)
* 标签使用必须符合标签嵌套规则。( `div` 不得置于 `p` 中，`tbody` 必须置于 `table` 中。)
* HTML 标签的使用应该遵循标签的语义。
* 尽可能少的使用无语义的标签div和span；
* 在语义不明显时，既可以使用div或者p时，尽量用p, 因为p在默认情况下有上下间距，对兼容特殊终端有利；
* 不要使用纯样式标签，如：b、font、u等，改用css设置。

```
下面是常见标签语义
- p - 段落
- h1,h2,h3,h4,h5,h6 - 层级标题
- strong,em - 强调
- q - 引用
- blockquote - 一段或长篇引用
- ul - 无序列表
- ol - 有序列表
- dl,dt,dd - 定义列表
- header - “网页”或“section”的页眉
- footer - “网页”或“section”的页脚
- nav - 页面的导航链接区域
- section - 文档中的“节”或“段”
```

## 属性
* 属性名必须使用小写字母。
* 属性值必须用双引号包围。

```html
<!-- good -->
<script src="esl.js"></script>

<!-- bad -->
<script src='esl.js'></script>
```

* 布尔类型的属性，建议不添加属性值。(disabled、checked)

## 样式文件表
* 非特殊情况下样式文件须放至`<head>`。
* 慎用@import导入样式文件。 PS:造成无法同时下载不同的样式文件（如果这个主题有多个样式文件），会增加页面总体加载时间，
  网络状况不好的情况下，刚开始的几秒中会很混乱。

## 通用
* 启用 IE Edge 模式。
* 指定字符编码的 `meta` 必须是 `head` 的第一个直接子元素。
* 让国内的双核浏览器用`webkit`的内核来渲染
* 网页优先采用Chrome渲染
```html 
<!DOCTYPE html>
<html lang="zh-cmn-Hans">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
  <!-- 其中http-equiv=”X-UA-Compatible”这个是IE8的专用标记，是用来指定Internet Explorer 8 浏览器模拟某个特定版本IE浏览器的渲染方式，
  以此来解决IE浏览器的兼容问题。     -->
	<meta name="renderer" content="webkit">
</head>
```
*  `JavaScript` 应当放在页面末尾，或采用异步加载。
* 在 `head` 中引入页面需要的所有 `CSS` 资源
* 省略协议。使用`<script src="//xxx"></script>`而不是`<script src="http://xxx"></script>`
* 重要图片必须加上alt属性; 给重要的元素和截断的元素加上title。
* 在支持 `HTML5` 的浏览器中优先使用 `audio` 和 `video` 标签来定义音视频元素。
* 在页面模块的开始和结束加注释(以便其他人对模块一目了然)

```html
<!-- loding弹出层 start -->
<div class="loding">...</div>
<!-- loding弹出层 end -->
```



