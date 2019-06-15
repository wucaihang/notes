# 概述
W3C万维网联盟制定：HTML-结构（骨骼）、CSS-表现（外观）、JS-行为（运动）
1. C/S & B/S
1. HTML（Hypertext Markup Language）
超文本：将生活中的文字、声音、图片、视频等信息以文本形式存储在计算机中
1. 抛出：
    - 记事本中调大字体，在写字板中是否变大（SEO认为网页只应该存在一个`H1`元素）
    - 改后缀用浏览器查看（资源管理器隐藏后缀）
1. 标题标签。查看源代码

# 基本标签
1. HTML文档标准结构
1. 注释 
1. 字体标记引出属性。学会查[W3School手册](https://www.w3cschool.cn/htmltags/)
1. `doctype`：编码浏览器进入兼容（怪异）模式  
93年6月1.0，95年11月2.0，97年1月3.2，99年12月4.01,2000年1月XHTML，14年10月5.0（`<!DOCTYPE html>`）
1. [`meta`](https://www.w3cschool.cn/htmltags/tag-meta.html)：利用IDE出现乱码（二战电报密码），字符集，空元素
    - charset
    - name:content：keywords、description
    - http-equiv:content：refresh、content-type、expires、charset、set-cookie
    ```html
    <meta http-equiv="refresh" content="5;url=http://www.baidu.com" />
    ```
1. `p`、`br`：空白字符与换行（诗句）
1. `&nbsp`;：[实体](https://www.w3cschool.cn/htmltags/html-symbols.html)，转义
1. `b`、`i`、`u`、`s`
1. `img` src：相对路径/绝对路径，大小，格式（JPEG、PNG、GIF颜色少）  
IE6遇到png-24透明部分发灰不透明，解决办法1.转换为png-8；2.引入外部繁琐的JS代码，自行百度
# HTML语法特点
1. 注释不能嵌套
1. 元素可以嵌套
1. *不区分大小写*
1. *属性可以没有值，属性值可以没有引号*
1. *元素可以没有结束，可以交叉*
# 一些属性
1. title    鼠标悬停提示
1. for  焦点关联元素
# 其他标签
1. `center`、`hr`、`fieldset`、`legend`
1. `iframe` src
1. `frameset`(不能有body、支持嵌套)：rows(%, *, %...)、cols（%, %...）
    - `frame`：src
1. `a` href(、#、mailto:)、target(_blank、_parent、**_self**、_top、framename)、name/id
1. `table`：border-spacing、  
`th`、`thead`、`tbody`(默认浏览器会为table自动添加tbody)、`tfoot`(这三个标签无论书写顺序如何，显示顺序不变)、colspan
## 文本标签
1. `strong` 重要 粗体
1. `em` 强调 斜体
1. `small` 细则 小一号
1. `big` 
1. `cite` 参考/引用(书名号) 斜体
1. `q` 行内短引用 自动加引号(通过:before/:after添加，不通用)
1. `blockquote` 长引用 块级引用(独占一行)
1. `sub`/`sup`
1. `del` 删除线
1. `ins` 插入内容 下划线
1. `pre`  原格式输出
1. `code` 代码 不保留格式
## 列表标签
1. `ul` type：**disc**、square、circle（各浏览器默认表现不一致）
1. `ol` type：**1**、a、A、i、I
1. `dl` dt dd相对dt再缩进
## 表单标签
1. `form`：method、action
1. `input`：type(**text**、password、radio、checkbox、submit、reset、button)、name(如果希望表单提交此项数据，必须指定name属性)、value、checked、placeholder(提示文本，IE8以下不支持)
1. `select`：multiple（**simple**、multiple）
    - `option`：selected
    - `optgroup`：label
1. `textarea`：cols、rows
1. `button`：type(**submit**、reset、button)
1. `label`：for
# 块元素&内联元素
1. 块元素：`div`、p、h1、center、form、fieldset、hr、table、ul、ol  
p元素不能包含其他块元素
1. 内联元素：a、b、u、i、br、font、img、input、select、`span`  
a元素不能嵌套a


[视频链接](https://www.bilibili.com/video/av34069180/?p=1)
[友情链接](https://space.bilibili.com/11890920?spm_id_from=333.788.b_765f7570696e666f.2)