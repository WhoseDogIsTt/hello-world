# 欢迎使用 markdown在线编辑器 mdeditor

**markdown是一种轻量级的「标记语言」**


![markdown](https://www.mdeditor.cn/images/logos/markdown.png "markdown")


markdown是一种可以使用普通文本编辑器编写的标记语言，通过简单的标记语法，它可以使普通文本内容具有一定的格式。它允许人们使用易读易写的纯文本格式编写文档，然后转换成格式丰富的html页面，markdown文件的后缀名便是“.md”


## mdeditor是一个在线编辑markdown文档的编辑器

*mdeditor扩展了markdown的功能（如表格、脚注、内嵌html等等），以使让markdown转换成更多的格式，和更丰富的展示效果，这些功能原初的markdown尚不具备。*

> markdown增强版中比较有名的有markdown extra、multimarkdown、 maruku等。这些衍生版本要么基于工具，如~~pandoc~~，pandao；要么基于网站，如github和wikipedia，在语法上基本兼容，但在一些语法和渲染效果上有改动。

mdeditor源于pandao的javascript开源项目，开源地址[editor.md](https://github.com/pandao/editor.md "editor.md")，并在mit开源协议的许可范围内进行了优化，以适应广大用户群体的需求。向优秀的markdown开源编辑器原作者pandao致敬。


![pandao editor.md](https://www.mdeditor.cn/images/logos/editormd-logo-180x180.png "pandao editor.md")



## mdeditor的功能列表演示

# 标题h1

## 标题h2

### 标题h3

#### 标题h4

##### 标题h5

###### 标题h5

### 字符效果和横线等

----

~~删除线~~ <s>删除线（开启识别html标签时）</s>
*斜体字*      _斜体字_
**粗体**  __粗体__
***粗斜体*** ___粗斜体___

上标：x<sub>2</sub>，下标：o<sup>2</sup>

**缩写(同html的abbr标签)**

> 即更长的单词或短语的缩写形式，前提是开启识别html标签时，已默认开启

the <abbr title="hyper text markup language">html</abbr> specification is maintained by the <abbr title="world wide web consortium">w3c</abbr>.

### 引用 blockquotes

> 引用文本 blockquotes

引用的行内混合 blockquotes
                    
> 引用：如果想要插入空白换行`即<br />标签`，在插入处先键入两个以上的空格然后回车即可，[普通链接](http://localhost/)。

### 锚点与链接 links

[普通链接](http://localhost/)

[普通链接带标题](http://localhost/ "普通链接带标题")

直接链接：<https://github.com>

[锚点链接][anchor-id] 

[anchor-id]: http://www.this-anchor-link.com/

gfm a-tail link @pandao

> @pandao

### 多语言代码高亮 codes

#### 行内代码 inline code

执行命令：`npm install marked`

#### 缩进风格

即缩进四个空格，也做为实现类似`<pre>`预格式化文本(preformatted text)的功能。

    <?php
        echo "hello world!";
    ?>

预格式化文本：

    | first header  | second header |
    | ------------- | ------------- |
    | content cell  | content cell  |
    | content cell  | content cell  |

#### js代码　

```javascript
function test(){
	console.log("hello world!");
}
 
(function(){
    var box = function(){
        return box.fn.init();
    };

    box.prototype = box.fn = {
        init : function(){
            console.log('box.init()');

			return this;
        },

		add : function(str){
			alert("add", str);

			return this;
		},

		remove : function(str){
			alert("remove", str);

			return this;
		}
    };
    
    box.fn.init.prototype = box.fn;
    
    window.box =box;
})();

var testbox = box();
testbox.add("jquery").remove("jquery");
```

#### html代码 html codes

```html
<!doctype html>
<html>
    <head>
        <mate charest="utf-8" />
        <title>hello world!</title>
    </head>
    <body>
        <h1>hello world!</h1>
    </body>
</html>
```

### 图片 images

image:

![](https://www.mdeditor.cn/examples/images/4.jpg)

> follow your heart.

![](https://www.mdeditor.cn/examples/images/8.jpg)

> 图为：厦门白城沙滩

图片加链接 (image + link)：

[![](https://www.mdeditor.cn/examples/images/7.jpg)](https://www.mdeditor.cn/examples/images/7.jpg "李健首张专辑《似水流年》封面")

> 图为：李健首张专辑《似水流年》封面

----

### 列表 lists

#### 无序列表（减号）unordered lists (-)

- 列表一
- 列表二
- 列表三
  
#### 无序列表（星号）unordered lists (*)

* 列表一
* 列表二
* 列表三

#### 无序列表（加号和嵌套）unordered lists (+)

+ 列表一
+ 列表二
    + 列表二-1
    + 列表二-2
    + 列表二-3
+ 列表三
    * 列表一
    * 列表二
    * 列表三

#### 有序列表 ordered lists (-)

1. 第一行
2. 第二行
3. 第三行

#### gfm task list

- [x] gfm task list 1
- [x] gfm task list 2
- [ ] gfm task list 3
    - [ ] gfm task list 3-1
    - [ ] gfm task list 3-2
    - [ ] gfm task list 3-3
- [ ] gfm task list 4
    - [ ] gfm task list 4-1
    - [ ] gfm task list 4-2
                
----

### 绘制表格 tables

| 项目        | 价格   |  数量  |
| --------   | -----:  | :----:  |
| 计算机      | $1600   |   5     |
| 手机        |   $12   |   12   |
| 管线        |    $1    |  234  |

first header  | second header
------------- | -------------
content cell  | content cell
content cell  | content cell 

| first header  | second header |
| ------------- | ------------- |
| content cell  | content cell  |
| content cell  | content cell  |

| function name | description                    |
| ------------- | ------------------------------ |
| `help()`      | display the help window.       |
| `destroy()`   | **destroy your computer!**     |

| left-aligned  | center aligned  | right aligned |
| :------------ |:---------------:| -----:|
| col 3 is      | some wordy text | $1600 |
| col 2 is      | centered        |   $12 |
| zebra stripes | are neat        |    $1 |

| item      | value |
| --------- | -----:|
| computer  | $1600 |
| phone     |   $12 |
| pipe      |    $1 |

----

#### 特殊符号 html entities codes

&copy; &  &uml; &trade; &iexcl; &pound;
&amp; &lt; &gt; &yen; &euro; &reg; &plusmn; &para; &sect; &brvbar; &macr; &laquo; &middot; 

x&sup2; y&sup3; &frac34; &frac14;  &times;  &divide;   &raquo;

18&ordm;c  &quot;  &apos;

### emoji表情 :smiley:

> blockquotes :star:

#### gfm task lists & emoji & fontawesome icon emoji & editormd logo emoji :editormd-logo-5x:

- [x] :smiley: @mentions, :smiley: #refs, [links](), **formatting**, and <del>tags</del> supported :editormd-logo:;
- [x] list syntax required (any unordered or ordered list supported) :editormd-logo-3x:;
- [x] [ ] :smiley: this is a complete item :smiley:;
- [ ] []this is an incomplete item [test link](#) :fa-star: @pandao; 
- [ ] [ ]this is an incomplete item :fa-star: :fa-gear:;
    - [ ] :smiley: this is an incomplete item [test link](#) :fa-star: :fa-gear:;
    - [ ] :smiley: this is  :fa-star: :fa-gear: an incomplete item [test link](#);

#### 反斜杠 escape

\*literal asterisks\*
            
### 科学公式 tex(katex)

$$e=mc^2$$

行内的公式$$e=mc^2$$行内的公式，行内的$$e=mc^2$$公式。

$$\(\sqrt{3x-1}+(1+x)^2\)$$
                    
$$\sin(\alpha)^{\theta}=\sum_{i=0}^{n}(x^i + \cos(f))$$

多行公式：

```math
\displaystyle
\left( \sum\_{k=1}^n a\_k b\_k \right)^2
\leq
\left( \sum\_{k=1}^n a\_k^2 \right)
\left( \sum\_{k=1}^n b\_k^2 \right)
```

```katex
\displaystyle 
    \frac{1}{
        \bigl(\sqrt{\phi \sqrt{5}}-\phi\bigr) e^{
        \frac25 \pi}} = 1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {
        1+\frac{e^{-6\pi}}
        {1+\frac{e^{-8\pi}}
         {1+\cdots} }
        } 
    }
```

```latex
f(x) = \int_{-\infty}^\infty
    \hat f(\xi)\,e^{2 \pi i \xi x}
    \,d\xi
```

### 绘制流程图 flowchart

```flow
st=>start: 用户登陆
op=>operation: 登陆操作
cond=>condition: 登陆成功 yes or no?
e=>end: 进入后台

st->op->cond
cond(yes)->e
cond(no)->op
```

### 绘制序列图 sequence diagram

```seq
andrew->china: says hello 
note right of china: china thinks\nabout it 
china-->andrew: how are you? 
andrew->>china: i am good thanks!
```

### END
