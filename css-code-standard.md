# css代码风格

## 缩进
* 代码缩进使用4个空格
* `:`后有一个空格
* `{`前有一个空格
* `}`要另起一行
* 多个选择器公用一段样式时，每个选择器都要占一行 

```css
.m-nav,
.g-header,
.u-btn-danger {
    position: absolute;
}
```

## 样式声明顺序
* Positioning --布局方式、位置，相关属性包括：position, top, z-index, display, float等。
* Box Model -- 盒模型，相关属性包括：width, height, padding, margin，border,overflow。
* Typographic -- 文本排版，相关属性包括：font, line-height, text-align。
* Visual -- 外观，相关属性包括：color, background, list-style, transform, animation。
* Misc -- 其他。
（此声明顺序可以减少浏览器的reflow，参考：https://blog.csdn.net/sinat_37328421/article/details/54575638）

```css
.declaration-order {
    /* Positioning */
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 100;

    /* Box-model */
    display: block;
    float: right;
    width: 100px;
    height: 100px;

    /* Typography */
    font: normal 13px "Helvetica Neue", sans-serif;
    line-height: 1.5;
    color: #333;
    text-align: center;

    /* Visual */
    background-color: #f5f5f5;
    border: 1px solid #e5e5e5;
    border-radius: 3px;

    /* Misc */
    opacity: 1;
}
```
## 命名
* 根据相应模块或部件的内容或功能命名，（不应该出现什么.right、.left之类歧义很大的类名）。
* 长名称或词组可以使用"-"来为选择器命名。
* 不要使用 " _ " 下划线在前来命名css。（能良好的区分javascript变量名，浏览器兼容性问题（比如使用_tips的选择器命名，在IE6是无效的））。
* 可以采用BEM方式来命名,模块名（Block）-元素名(Element)-修饰器名(Modifier)（参考：https://bemcss.com/）。

## last
* 一律小写。
* 尽量不用缩写，缩写应该一眼就能明白意思。（比如：btn之类）
* 不要随便使用id。
* 去掉小数点前面的0： 0.9rem => .9rem  0px => 0。
* 去掉属性值为0的单位。
* 使用简写：margin： 0 1rem 3rem。


