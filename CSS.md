# 概述
层叠样式表（Cascading Style Sheets），祖先元素的样式（background相关、border相关、position相关、overflow等除外）会向下继承，相同样式局部优先，同一优先级后续优先
# 引入方式
1. 嵌入式：元素的style属性
1. 内联式：在head的style元素中编写
1. 外联式：在head中link元素引入外部CSS文件(共用、缓存)
    ```html
    <link rel="stylesheet" type="text/css" href="xxx.css" />
    ```
# 语法
1. 注释：/* */
1. 构成：选择器、声明块（键值对，以分号分割）
    - 字符串无需引号包围，有空格的字符串需要引号
    - [单位](https://www.w3cschool.cn/cssref/css-units.html)
        - px    像素
        - em    相对于字体大小 1em=1font-size
        - %     相对父元素大小
    - [颜色](https://www.w3cschool.cn/cssref/css-colors.html)
        - colorname
        - #FFFFFF
        - #FFF
        - rgb(255, 255, 255)
        - rgb(100%, 100%, 100%)

# [选择器](https://www.w3cschool.cn/cssref/53s812dp.html)
匹配哪些内容会被声明块的样式影响
1. 元素选择器
1. ID选择器：#
1. class选择器：. 
1. 通配符选择器：*
1. 并集选择器：,
1. 交集选择器：p.fire
1. 祖孙选择器：p .fire
1. 父子选择器：>    (IE6不支持)
1. 后续所有兄弟选择器：~
1. 后续第一个兄弟选择器：+
1. 伪类选择器
    - :first-child
    - :last-child
    - :only-child
    - :nth-child(1)
    - :first-of-type
    - :last-of-type
    - :only-of-type
    - :nth-of-type(2n) ：还可以传递even、odd
    - :empty
    - :not(select)
    - :link
    - :hover(IE6以外还支持a以外的元素)
    - :active(IE6以外还支持a以外的元素)
    - :visited(只能设置字体颜色color(IE6除外))
    - :focus
    - :blur
    - ::selection：双冒号，被选中的文字（早期火狐::-moz-selection）
    - :first-letter
    - :first-line
    - :before   第一个子元素之前（一般与content结合使用）
    ```css
    a:before{ content:attr(href); }
    ```
    - :after    最后一个子元素之后
1. 属性选择器
    - []
    - [=]
    - [*=]、
    - [^=]
    - [$=]
    - [~=]  包含完整单词
    - [|=]  以完整单词（或-拼接的一部分）开头
## 选择器优先级
内联    1000  
id      100  
类&伪类 10  
元素    1  
`*`       0  
继承    没有优先级  
- 组合选择器  优先级相加再判断（n个同级别相加始终不会超过上一级）
- 并集选择器  不会相加，各自独立
- 强制优先    `!important`最高优先级(不推荐)
- 超链接伪类选择器  优先级一致，所以hover不能写在active后面，link和visited不能写在hover后面
    ```css
    p { color: green !important; }
    ```
# 常用属性
1. `color`：文字前景色
1. `background`：没有顺序和数量要求，不写取默认值  
背景颜色和图片可以同时指定，颜色一定是在图片下
    - `background-color`：**transparent**
    - `background-image`: url() 雪碧图可以减少请求次数，可以避免惰性加载出现的闪烁
    - `background-repeat`：**repeat**、repeat-x、reapeat-y、no-repeat
    - `background-position`：
        - **0% 0%**（只写一个，另一个默认50%）
        - 0px 0px（只写一个，另一个默认50%）
        - top left、center center...(只写一个单词，另一个默认center)
    - `background-attachment`：**scroll**、fixed（定位相对于浏览器窗口）
1. [`font`](https://www.w3cschool.cn/cssref/pr-font-font.html)：font-style、font-variant、font-weight、font-size/line-height、font-family  
size和family必须在后两位，其他顺序无要求，也可以没有
    - `font-size`：区域高度，Chrome最小支持到12px
    - `line-height`：20px、120%（相对于font-size）、1.2。通过设置行高间接控制行间距  
    *line-height:1*   可以使当行文本在父容器中垂直居中显示
    - `font-family`：客户端系统不支持使用默认字体，可以指定多个字体，用逗号分隔，左侧优先。可以在最后指定字体大类，他不是具体的字体，由系统自行选择（火狐特殊）。
        - serif 衬线字体，常用(笔尾勾笔，笔画宽窄不一)
        - sans-serif 非衬线字体(横平竖直，粗细一致)
        - monospace 等宽字体(英文字体跨度一致)
        - cursive 草书字体(英文)
        - fantasy 虚幻字体(英文)
    - `font-style`：**normal**、italic、oblique
    倾斜
    - `font-weight`：**normal**、bold、bolder、lighter、100~900（normal400、bold700）
    - `font-variant`：**normal**、small-caps小写字母以小型大写字母显示
1. `text-transform`：**none**、capitalize、uppercase、lowercase
1. `text-decoration`：**none**、underline、overline、line-through删除线、blink
1. `text-align`：**left**、right、center、justify
1. `text-indent: 2em`：首行缩进，负值首行悬停
1. `letter-spacing`: 正负数、百分比。支持中文
1. `word-spacing`
1. `list-style`：none
# [盒子模型](https://www.w3cschool.cn/css/css-boxmodel.html)
CSS认为每个元素的显示都是一个box区域(落地成盒)
1. content
    - `width`
    - `height`
1. [`border`](https://www.w3cschool.cn/css/css-border.html)：无顺序要求，不能分别指定四边
    1. `border-width`：上 右 下 左、上 左右 下、上下 左右、all
    2. `border-color`：
    3. `border-style`：**none**、hidden解决表格边框冲突、dotted点线、dashed虚线(有些呈现实线)、solid实线、double双实线、groove双边凸右下光、ridge双边凸左上光、inset单边凸右下光、outset单边凸左上光
    - `border-left`：单独指定一边
    - `border-left-style`
1. `padding`
    - `pading-bottom`
1. `margin`：不影响元素可见区域大小，影响元素位置。  
**相邻**的兄弟元素间的**垂直**方向外边距会重叠取最大值，不会叠加  
    ```css
    margin：0 auto;  /* 水平居中，auto使空白最大占据剩余空间 */
    ```
    - `margin-top`

## 清除默认边距
ul、ol等有默认内外边距
```css
* { margin: 0; padding: 0; }
```
## 内联元素与盒子模型
1. 不支持`width`/`height`  
1. 垂直方向的边框、内边距都会覆盖其他元素
1. 水平方向外边距会叠加，不支持垂直方向外边距
# 浮动
1. `float`脱离文档流：**none**、left、right  
    - 文档流：默认块元素高度被内容撑开，宽度auto自上而下独占一行，内联元素宽高被内容撑开，从左到右排列
    - 浮动元素默认宽高由内容撑开
    - 浮动元素无论块元素还是内联元素，表现一致
    - 浮动元素遇到父容器边界或其他浮动元素就会停靠
    - 浮动元素始终不会超过它前面的兄弟元素（无论兄弟元素是否浮动）
    - 文字环绕：浮动元素可能会盖住其他文档流元素，但是不会盖住文档流元素的文字内容
1. `clear`清除浮动，其他兄弟浮动元素不影响当前元素：**none**、left、right、both 
### 高度塌陷
子元素浮动后，不再撑开父容器（需要自行设置大小）  
W3C标准中（IE6不支持），元素都有一个隐含属性BFC（Block Formatting Context），默认是关闭的。开启方法
- 设置元素浮动
- 设置元素绝对定位
- 设置display为inline-block 
- 设置**overflow**为非visible（推荐）
- 利用父容器的:after选择器（推荐）
```css
.clearfix:before, .clearfix:after {
    content: "";
    display: table;  /* block不能解决子元素margin影响父元素的问题 */
    clear: both;
}
```  
打开BFC之后具有如下特性：
- 父元素的垂直外边距不会和子元素重叠
- 不会被浮动元素覆盖（出现在右侧）
- 可以包含浮动子元素  

IE6要开启hasLayout，方法有很多：
- `zoom`缩放属性为1（推荐）
- 为元素指定宽度（推荐）

# CSS Hack
解决兼容性，不易维护，不建议使用
## 条件Hack
IE10及以上版本已不支持   
- `<!-- if IE -->`    只在所有IE中显示  
- `<!-- if IE 6 -->`  只在所有IE6中显示
```html
    <!-- if lte IE 6 -->
    lt小于，gte大于等于，!非此版本
    <![endif]-->
```
## 属性级Hack
- _：选择IE6及以下`_color：#092;`
```css
/* 解决IE6中，input text与textarea的内容过多会让背景图片滚动的问题 */
_background-attachment: fixed;
```
- *：选择IE7及以下`*color: #092;`
- \9：选择IE6+`color: #092\9;`
- \0：选择IE8+和Opera15以下
## 选择器Hack
- 在选择器前加【* 】匹配IE6及以下
- 【* + 】匹配IE7

# 其他相关属性
1. [`display`](https://www.w3cschool.cn/cssref/pr-class-display.html)：none（不再空间）、block、inline、inline-block行内块（类似img，即支持宽高又不独占一行）、list-item、table（表现为table的块元素，解决子元素margin影响父元素的问题）
1. `visibility`：**visible**、hidden（不显示但占空间）
1. `overflow`：**visible**、hidden、scroll(始终有两个滚动条)、auto
1. `text-overflow`：
1. `position`：
    - absolute  相对于第一个非static祖先元素(脱离文档流，提升一个层级)
    - fixed 相对于浏览器窗口(特殊的absolute，不随页面滚动，IE6不支持)
    - relative  相对于自己的正常位置(不脱离文档流，提升一个层级)
    - **static**    正常流位置（不支持`top`/`left`/`bottom`/`right`/`z-index`属性）
1. `z-index`：显示提升层级，值越大越靠前（子元素始终在父元素前面）
1. `opacity`：0~**1**（IE8及以下不支持，filter: alpha(opacity=50)）
1. `border-collapse`：collapse（表格）边框合并、**separate**独立的
1. `resize`：none避免textarea等可拖拽大小破坏布局
1. `cursor`：**auto**浏览器设置、url、default（箭头）、crosshair(十字)、pointer(手型鼠标)、move。ne-resize、text、wait、help

# 压缩
压缩CSS、JS、图片等，雪碧图集

总结坑：
1. 默认内外边距
1. 超链接直接的换行被作为一个空白显示
1. 浏览器默认line-height
1. IE6
    - 不支持父子选择器
    - hover和active伪类选择器只支持a元素
    - 解决高度塌陷是 `zoom:1`
    - 不支持 `position:fixed`
    - text-indent会让背景右移
    - 向左/右浮动的元素设置左/右外边距时，外边距会呈现双倍效果：解决 `display:inline`
    - 提供了Hack解决与其他浏览器的兼容差异