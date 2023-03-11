  [//]: // (作者：JinyuLi)
  [//]: // (日期：2023.03.11)
  [//]: // (内容：LaTeX中文字的基本使用)

# LaTeX分享【LaTeX中文字的基本使用】

>作者：JinyuLi
>
>日期：2023.03.11
>
>内容：LaTeX中文字的基本使用，主要从字号，字族以及文字样式（颜色和下划线之类的），并分享几个文字宏包
>>1、LaTeX中英文混合排版
>>2、LaTeX中文字的基本手法————大小、字体样式、字体类型
>>3、几个有意思的字体宏包

本文观前提醒：*文章参考网络博文整理并根据自身理解而成，文末附博文链接，如果打不开或许是因为是外语资料，请自行学会“科学上网”本文不做详解。*

## LaTeX中英文混合排版

### 宏包引入

在上文中，我们曾经说过，LaTeX中有一个很重要的概念----**宏包**，我们在LaTeX中要使用什么样式的排版，要插入什么内容都和宏包有着密不可分的关系，*如果没看过的话，也欢迎大家使用下面链接跳转访问*

[LaTeX源文档结构及通用手法](https://mp.weixin.qq.com/s/69YMNP4gGGxJgwI5qcvf9w)
> <https://mp.weixin.qq.com/s/69YMNP4gGGxJgwI5qcvf9w>

而在这一篇文档中，我打算和大家分享一下文字的通用使用方式的话，就避不开一个东西，那就是中英混排（毕竟我所生长的环境是中文语境，写的文档也多是中文文档，故而很难避开这个话题），为什么要专门把中英混排放在这里讲一下呢？首先，LaTeX是一个美国的东西吧，而这个东西很自然而然，它本身是不支持中文的，这就很让人头大，但是，没关系，总有人会去做一个中文宏包来支持中文排版的，这个宏包就是我想分享给大家的————**CTEX**宏包

为了给大家说明地更加清楚，我们可以看看下面这两张图片

![有无插入ctex宏包的对比]("有无插入ctex宏包的对比")

如果我们选用"PDFLaTeX"进行编译的话，我们会发现，第一份代码会出现直接的报错，而第二份虽然会出现警告（主要原因是因为TeXLive本身的版本问题的原因）但是依然可以成狗编译出来，其中最主要的原因就在于这两个是否有**ctex**宏包的存在，而这个ctex宏包正是告诉LaTeX我们要准备进行中英文混排的先前预警，我添加了这个工具以后，就能在文档中快乐撰写中文了。

而关于ctex更加详细的介绍，大家也可以在文末的参考文章处，点击**宏包ctex的官方手册**链接，进行跳转学习。接下来，我们引入了ctex宏包以后，具备了在LaTeX中继续编撰中文的资格了，那么就开始写下我们的第一个LaTeX文档了。

## LaTeX中文字的基本手法————大小、字体样式、字体类型

### 插入文字

无论撰写什么类型的LaTeX文档，我们总要首先进行三步操作**文档类型声明、宏包引入、正文区声明**（这些操作，都在我的这个专栏前面的专栏提到过，大家可以自行在参考文章*LaTeX源文档结构及通用手法*跳转阅读）

那我们首先进行这三布操作，源代码如下：

'''
\documentclass{article}   % 文档声明

\usepackage{a4}           % 引用宏包 a4 设置文档版面大小为a4纸张大小
\usepackage{ctex}         % 引用宏包 ctex 使得文档具有中英混排效果

\begin{document}          % 标签 \begin{document} 开始正文撰文区域

% 这里填写正文内容 %

\end{document}            % 标签 \end{document} 结束正文撰文区域
'''

大家可以很容易就能理解，其中的'\begin{document} \end{document}'中间的空白部分就是我们写入正文的内容区域，那理解以后，我们新建一个 *.tex* 文档，把我上面的代码整CV进去，然后把 *% 这里填写正文内容 %* 替换成 **Hello World 你好世界** 让我们的第一个LaTeX文档向世界问个好，效果如下：

![Hallo World](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExZGYzMzkxZmM3YmUxNDE0ZGRiY2M2NDZhNzExZWY4MDcwNzlkZTQ2OSZjdD1n/qd5tVzf8tVb13lzKpH/giphy.gif "Hello World")

这样，就是LaTeX里面对于文字的最基本的操作，插入字体，**在正文区** 中只要把你所需要输入的文字插入即可。

### 文字大小————字号

对于LaTeX来说调整文档内的字号个人习惯于两种方式，一种是采用“全局控制，在需要特殊处理处给予特殊处理。”还有一种是“需求多变类型，不同的文字字段选用不同的字号”，当然，我最常用的还是第一种了，毕竟我没有什么文档是需要不断变更文字字段的字号大小的。无论是哪种变更字号的方式，我们都需要引入包去使用，这里我们使用的包的名称是**fontsize**用法也是很简单，只要在导言区'\usepackage{fontsiz}'即可，具体调整字号的方法见下。

那么既然有两种，那么我们可以分成两部分：

#### 1、全局控制，在需要特殊处理处给予特殊处理

我们可以直接在**文档声明**部分就确定全局字体的基本大小，如下：

![字号全局设置](https://pic4.58cdn.com.cn/nowater/webim/big/n_v24a2ec468011242cfbe112ed9daaa10a2.png "字号全局设置")

这样，我们就设置好了全文的字体的字体基本大小

#### 2、需求多变类型，不同的文字字段选用不同的字号

## 几个有意思的字体宏包

## 参考文章

[宏包ctex的官方手册](https://ctan.org/pkg/ctex)
> <https://ctan.org/pkg/ctex>
------
[LaTeX源文档结构及通用手法](https://mp.weixin.qq.com/s/69YMNP4gGGxJgwI5qcvf9w)
> <https://mp.weixin.qq.com/s/69YMNP4gGGxJgwI5qcvf9w>
------
[Latex字体大小](https://blog.csdn.net/yhcwjh/article/details/116516011)
> <https://blog.csdn.net/yhcwjh/article/details/116516011>
------
[Latex字体大小](https://blog.csdn.net/yhcwjh/article/details/116516011)
> <https://blog.csdn.net/yhcwjh/article/details/116516011>

大家也可以移步以下平台阅览本专栏，感谢

>微信公众号 **Jinyu Li OwO**

![推文公众号](https://pic6.58cdn.com.cn/nowater/webim/big/n_v289de6f6b045343b382e79ba62c813913.png "推文平台")

>[B站专栏](https://www.bilibili.com/read/cv21970159)
>><https://www.bilibili.com/read/cv21970159>
------
>[知乎](https://www.zhihu.com/column/c_1611528726348275712)
>> <https://www.zhihu.com/column/c_1611528726348275712>
------
>[CSDN](https://blog.csdn.net/ljy025/category_12214744.html)
>><https://blog.csdn.net/ljy025/category_12214744.html>

公众号更新
>周三（11：45） 周六（16：30）

其他平台不定期。