# meta标签到底是做什么的，我竟一无所知

## 1. 起因

最近部门在推微前端，需要按功能拆分多个子应用，主应用在加载的过程中经常出现加载失败的问题。因为https地址中，如果加载了http资源，浏览器将认为这是不安全的资源，将会默认阻止。后来在文档中添加了`<meta http-equiv="Content-Security-Policy" content="upgrade-insecure-requests">`完美解决。

此时我才发现自己对`meta`简直一无所知，本文主要介绍`meta`，顺带也会提一提`head`中的其它标签。如有不对请指出，最后欢迎点赞 + 收藏。

## 2. head 标签

`head`标签与`html`标签，`body`标签一样是一个文档必须的元素。

`head`标签用于定于文档头部信息，它是所有头部元素的容器。`head`中的元素可以引用脚本、指示浏览器在哪里找到样式表、提供元信息等等。

文档的头部描述了文档的各种属性和信息，包括文档的标题、在 Web 中的位置以及和其他文档的关系等。绝大多数文档头部包含的数据都不会真正作为内容显示给读者。

下面这些标签可用在 `head` 部分：`base`, `link`, `meta`, `script`, `style`, 以及 `title`。

`注意:`应该把 `head` 标签放在文档的开始处，紧跟在 `html` 后面，并处于 `body` 标签或 `frameset` 标签之前。

## 3. title 标签

`title` 定义文档的标题，它是 `head` 部分中唯一必需的元素。浏览器会以特殊的方式来使用标题，设置的内容不会显示在页面中，通常把它放置在浏览器窗口的标题栏或状态栏上，如设置为空标题展示当前页面的地址信息。

当把文档加入用户的链接列表或者收藏夹或书签列表时，标题将成为该文档链接的默认名称。

### 1. dir 属性

规定元素中内容的文本方向`rtl`、`ltr`。

### 2. lang 属性

规定元素中内容的语言代码。

## 4. meta 标签

`meta` 元素往往不会引起用户的注意，但是`meta`对整个网页有影响，会对网页能否被搜索引擎检索，和在搜索中的排名起着关键性的作用。

`meta`有个必须的属性`content`用于表示需要设置的项的值。

`meta`存在两个非必须的属性`http-equiv`和`name`, 用于表示要设置的项。

比如`<meta http-equiv="Content-Security-Policy" content="upgrade-insecure-requests">`,设置的项是`Content-Security-Policy`设置的值是`upgrade-insecure-requests`。

### 1. http-equiv 属性

`http-equiv`一般设置的都是与`http`请求头相关的信息，设置的值会关联到http头部。也就是说浏览器在请求服务器获取`html`的时候，服务器会将`html`中设置的`meta`放在响应头中返回给浏览器。常见的类型比如`content-type`, `expires`, `refresh`, `set-cookie`, `window-target`, `charset`， `pragma`等等。

#### 1. content-type

比如：`<meta http-equiv="content-type" content="text/html charset=utf8">`可以用来声明文档类型，设置字符集，`content-type`几乎所有的属性都可以在`meta`中进行设置。

这样设置浏览器的头信息就会包含:

```
content-type: text/html charset=utf8
复制代码
```

#### 2. expires

用于设置浏览器的过期时间, 其实就是响应头中的expires属性。

```
<meta http-equiv="expires" content="31 Dec 2021">
复制代码
expires:31 Dec 2008
复制代码
```

#### 3. refresh

该种设定表示5秒自动刷新并且跳转到指定的网页。如果不设置url的值那么浏览器则刷新本网页。

```
<meta http-equiv="refresh" content="5 url=http://www.zhiqianduan.com">
复制代码
```

#### 4. window-target

强制页面在当前窗口以独立页面显示, 可以防止别人在框架中调用自己的页面。

```
<meta http-equiv="window-target" content="_top'>
复制代码
```

#### 5. pragma

禁止浏览器从本地计算机的缓存中访问页面的内容

```
<meta http-equiv="pragma" content="no-cache">
复制代码
```

### 2. name 属性

`name`属性主要用于描述网页，与对应的`content`中的内容主要是便于搜索引擎查找信息和分类信息用的, 用法与`http-equiv`相同，`name`设置属性名，`content`设置属性值。

#### 1. author

`author`用来标注网页的作者

```
<meta name="author" content="aaa@mail.abc.com">
复制代码
```

#### 2. description

`description`用来告诉搜素引擎当前网页的主要内容，是关于网站的一段描述信息。

```
<meta name="description" content="这是我的HTML">
复制代码
```

#### 3. keywords

`keywords`设置网页的关键字，来告诉浏览器关键字是什么。是一个经常被用到的名称。它为文档定义了一组关键字。某些搜索引擎在遇到这些关键字时，会用这些关键字对文档进行分类。

```
<meta name="keywords" content="Hello world">
复制代码
```

#### 4. generator

表示当前`html`是用什么工具编写生成的，并没有实际作用，一般是编辑器自动创建的。

```
<meta name="generator" content="vscode">
复制代码
```

#### 5. revised

指定页面的最新版本

```
<meta name="revised" content="V2，2015/10/1">
复制代码
```

#### 6. robots

告诉搜索引擎机器人抓取哪些页面，`all / none / index / noindex / follow / nofollow`。

```
<meta name="robots" content="all">
复制代码
```

`all`：文件将被检索，且页面上的链接可以被查询；`none`：文件将不被检索，且页面上的链接不可以被查询；`index`：文件将被检索；`follow`：页面上的链接可以被查询；`noindex`：文件将不被检索，但页面上的链接可以被查询；`nofollow`：文件将不被检索，页面上的链接可以被查询。

### 3. scheme 属性

`scheme` 属性用于指定要用来翻译属性值的方案。此方案应该在由 `head` 标签的 `profile` 属性指定的概况文件中进行了定义。`html5`不支持该属性。

## 5. base 标签

`base`标签定义了文档的基础`url`地址，在文档中所有的相对地址形式的`url`都是相对于这里定义的`url`而言的。为页面上的链接规定默认地址或目标。

```
<base href="http://www.w3school.com.cn/i/" target="_blank" />
复制代码
```

base标签包含的属性。

#### 1. href

`href`是必选属性，指定了文档的基础`url`地址。例如，如果希望将文档的基础URL定义为`https：//www.abc.com`，则可以使用如下语句：`<base href="http://www.abc.com">`如果文档的超链接指向`welcom.html`,则它实际上指向的是如下`url`地址：`https://www.abc.com/welocme.html`。

#### 2. target

定义了当文档中的`链接`点击后的打开方式`_blank`，`_self`，`_parrent`，`_top`。

## 6. link 标签

`link`用于引入外部样式表，在`html`的头部可以包含任意数量的`link`，`link`标签有以下常用属性。

```
<link type="text/css" rel="stylesheet" href="github-markdown.css">
复制代码
```

### 1. type

定义包含的文档类型，例如`text/css`

### 2. rel

定义`html`文档和所要包含资源之间的链接关系，可能的值有很多，最为常用的是`stylesheet`，用于包含一个固定首选样式的表单。

### 3. href

表示指向被包含资源的`url`地址。

## 7. style 标签

编写内部样式表的标签。

```
<style>
    body {
        background: #f3f5f9;
    }
</style>
复制代码
```

## 8. script 标签

加载`javascript`脚本的标签。加载的脚本会被默认执行。默认情况下当浏览器解析到`script`标签的时候会停止`html`的解析而开始加载`script`代码并且执行。

```
<script src="script.js"></script>
复制代码
```

### 1. type

指示脚本的`MIME`类型。

```
<script type="text/javascript">
复制代码
```

### 2. async

规定异步执行脚本，仅适用于通过`src`引入的外部脚本。设置的`async`属性的`script`加载不会影响后面`html`的解析，加载是与文档解析同时发生的。加载完成后立即执行。执行过程会停止`html`文档解析。

```
<script async src="script.js"></script>
复制代码
```

### 3. charset

规定在外部脚本文件中使用的字符编码。

```
<script type="text/javascript" src="script.js" charset="UTF-8"></script>
复制代码
```

### 4. defer

规定是否对脚本执行进行延迟，直到页面加载为止。设置了`defer`属性的`script`不会阻止后面`html`的解析，加载与解析是共同进行的，但是`script`的执行要在所有元素解析完成之后，`DOMContentLoaded`事件触发之前完成。

```
<script defer src="script.js"></script>
复制代码
```

### 5. language

规定脚本语言，与``type```功能类似，不建议使用该字段。

### 6. src

外部脚本的地址。

```
<script src="script.js"></script>
复制代码
```

## 9. bgsound

网站背景音乐。

```
<bgsound src="music.mp4" autostart="true" loop="5">
复制代码
```

### 1. src

表示背景音乐的`url`值。

### 2. autostart

是否自动播放`ture`自动播放，`false`不播放，默认为`false`。

### 3. loop

是否重复播放，值为数字或者`infinite`，表示重复具体次或无限次。

### 参考来源

- [1] **w3chool head**[1] **www.w3school.com.cn/tags/tag\_he…**[2] "w3c"
- [2] **head标签及子标签**[3] **blog.csdn.net/qq\_46580571…**[4] "Wangkiwa

``



关于本文

# 来源：隐冬

https://juejin.cn/post/6987919006468407309



The End

如果你觉得这篇内容对你挺有启发，我想请你帮我三个小忙：

1、点个 **「在看」**，让更多的人也能看到这篇内容

2、关注官网 **https://muyiy.cn**，让我们成为长期关系

3、关注公众号「高级前端进阶」，公众号后台回复 **「加群」** ，加入我们一起学习并送你精心整理的高级前端面试题。

![高级前端进阶](http://mmbiz.qpic.cn/sz_mmbiz_png/H8M5QJDxMHpg1ClH18gOQIicISIoSybyDNK203zFMpSM7jHdovb4elgdqNoy6Bylk7XicC6Rpj5QrCv3FkOpR6tw/0?wx_fmt=png)

**高级前端进阶**

接下来让我带你走进高级前端的世界，在进阶的路上，共勉！

48篇原创内容



Official Account

[》》面试官都在用的题库，快来看看《](https://mp.weixin.qq.com/s?__biz=MzA4Nzg0MDM5Nw==&mid=2247504782&idx=2&sn=4541e8493607653e84ede361999012c8&chksm=9031d06ca746597a1d0721e8216e81e646cf206f3b4952aaa2002bb7c39d44c04e834e1aaa85&mpshare=1&scene=1&srcid=0916cDJaipyErIrz9fa6eOXG&sharer_sharetime=1631790636212&sharer_shareid=35020dff9de3f73fa8209bb8cae057d6&key=601a5ac03618354fa6a2b439598488d613e5fbef82ed7e16f7b9ac18aaec29029f80b2f6d145472b972885518274a5f5fd5e1eaf9624f7f64bf0ddb67ed805ec1eb76723f15564826242c12359b49ee8b16801f369fd5a2603f32799358fdd301a985a64f6cb4c1590b96d7c8109f65c8ba92d9ee47dfa50bcd92c65a9ae2303&ascene=1&uin=MjQ5NDE3Nzk0MQ%3D%3D&devicetype=Windows+10+x64&version=63030073&lang=en&exportkey=Abr%2BHpoXEBZHCU3TtA6IBSo%3D&pass_ticket=1VXzIbDnK0kJ1tQBtduJa1dWyAdQuYFWv3x5Yjjr5h89%2Bqt5qBO2Pks%2BgevnS%2B51&wx_header=0&fontgear=2)《



```
“在看”吗？在看就点一下吧
```

[Read more](https://mp.weixin.qq.com/s?__biz=MzA4Nzg0MDM5Nw==&mid=2247504782&idx=2&sn=4541e8493607653e84ede361999012c8&chksm=9031d06ca746597a1d0721e8216e81e646cf206f3b4952aaa2002bb7c39d44c04e834e1aaa85&mpshare=1&scene=1&srcid=0916cDJaipyErIrz9fa6eOXG&sharer_sharetime=1631790636212&sharer_shareid=35020dff9de3f73fa8209bb8cae057d6&key=601a5ac03618354fa6a2b439598488d613e5fbef82ed7e16f7b9ac18aaec29029f80b2f6d145472b972885518274a5f5fd5e1eaf9624f7f64bf0ddb67ed805ec1eb76723f15564826242c12359b49ee8b16801f369fd5a2603f32799358fdd301a985a64f6cb4c1590b96d7c8109f65c8ba92d9ee47dfa50bcd92c65a9ae2303&ascene=1&uin=MjQ5NDE3Nzk0MQ%3D%3D&devicetype=Windows+10+x64&version=63030073&lang=en&exportkey=Abr%2BHpoXEBZHCU3TtA6IBSo%3D&pass_ticket=1VXzIbDnK0kJ1tQBtduJa1dWyAdQuYFWv3x5Yjjr5h89%2Bqt5qBO2Pks%2BgevnS%2B51&wx_header=0&fontgear=2##)

Reads 1988

ShareFavorite

Like20Wow7

People who shared this content also liked

世界第三大浏览器正在消亡

Likes 11

Java笔记虾

不喜欢

不看的原因

OK

- 内容质量低
-  

- 不看此公众号

Redis 16 种妙用场景

Reads 860

匠心零度

不喜欢

不看的原因

OK

- 内容质量低
-  

- 不看此公众号

session、token、jwt、oauth2 傻傻分不清

Reads 835

Java爱好者

不喜欢

不看的原因

OK

- 内容质量低
-  

- 不看此公众号

:，.VideoMini ProgramLike，轻点两下取消赞Wow，轻点两下取消在看