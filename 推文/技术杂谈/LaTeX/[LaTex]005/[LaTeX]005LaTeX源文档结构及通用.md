  [//]: // (作者：JinyuLi)
  [//]: // (日期：2023.03.07)
  [//]: // (内容：LaTeX源文档结构及通用手法)

# LaTeX分享【LaTeX源文档结构及通用手法】

>作者：JinyuLi
>
>日期：2023.03.07
>
>内容：LaTeX源文档结构及通用手法，本文主要简单和大家分享一下，我对于LaTeX源文档的文档结构，以及在使用LaTeX时的个人使用习惯，本文大致内容划分如下：
>>1、LaTeX源文件文档结构，**导言栏与正文区**
>-----
>>2、宏包（package）的个人理解
>-----
>>3、如何快速学习一个宏包的使用方法
>-----
>>4、参考文献

本文观前提醒：*文章参考网络内容部分在文末“参考文献”部分，如果打不开请自行学会“科学上网”本文不做详解。*

## LaTeX源文件文档结构，**导言栏与正文区**

在前面的文章中我们曾经提到过，LaTeX的源文件需要使用编译器进行编译以后才能生成PDF等可以广泛传播与符合个人使用的文件，而撰写LaTeX源文件其实更像是写代码一样。

而说到代码，大家最直观的感受就是，一片黑漆漆的背景，然后一行又一行的字符串，五颜六色的关键字，每行间有着大小不一的空格或者空行，就像下面这张图一样：

![code示意](https://th.bing.com/th/id/OIP.Yob1zCfmgDeYgoEB6ePZeQHaFG?pid=ImgDet&rs=1 "code示意")

很明显的可以看出，代码，是有着很清晰明了的结构的，那为什代码需要结构或者说架构呢，简单来说就是易读和易维护（修改），在写代码的过程中，我们最讨厌的就是看没有注释的代码，最讨厌的也是不写注释[Doge]

~~不可能好好写注释星人~~

![代码注释](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2pwZy92cWxiVkZsNUpuMjV1aG9vdkNZaHdQV0QzdGtsUVJFUGxwWmliSmIxT3BhRHNST3daUjdDUzFTd3lOZGpjSTlHZWljZ3dqV1k5SmliTDJ0NG5MVllJeG5jZy82NDA?x-oss-process=image/format,png "代码注释")

而清晰的代码的架构，就跟**注释**有着异曲同工之妙，有着让读者易于阅读和自己（或同事）易于维护的作用。虽然说LaTeX并不算编程语言

>在前文说过，LaTeX是一种基于 TeX 的排版系统。

但是毕竟LaTeX的源文件 *.tex* 文件也叫做“源代码”那跟代码沾边，那么LeTeX自然也可以有结构了。

对于LaTeX源文档的结构来说，一般类型的文档只要记住三个部分就行了，我个人一般是直接分为 **文档声明，导言，正文**

### 文档声明

文档声明主要是说明这个LaTeX是属于什么文档，因为在LaTeX中一般是有以下几种类型的文档

>1|| article：用于写短文，如期刊论文、技术报告、说明文档等。
>
>2|| report：用于写长文，如书籍、学位论文、年度报告等。
>
>3|| book：用于排版书籍，包括章节、目录、索引等。
>
>4|| letter：用于排版信件，包括信头、日期、收件人、寄件人、正文等。
>
>5|| beamer：用于制作幻灯片演示文稿。
>
>6|| memoir：类似于 report 类，但提供了更多的排版选项和命令，可用于编写各种类型的文档。

在LaTeX源文件中第一句就是要声明这个文档的类型，因为不同的文档类型所需要引入的“宏包”不尽相同，相关的语法也有相对的不同，而在其中引用的方法就是用'\documentclass[参数]{类型}' 的声明方法，实际的使用可以看看下面的这个图：

![code_1](https://pic8.58cdn.com.cn/nowater/webim/big/n_v21073d8bd439d400a872ddf92d0c116b4.png "code_1")

我们可以很容易的看出其中的用法：其中'12pt,UTF8'就是方括号中的内容就是这个文档的全局参数，'ctexart'就是大括号中的内容，就是这个文档的**类型**，在上面列出的文档类型中并没有出现ctexart这种文档类型并不需要感到奇怪，因为这是一种专门为中文定制的文档类型（这里就可以看出，除了上述列出的六种类型，LaTeX也是可以自定义文档类型的）而这里的**ctex**大家可以着重注意一下，因为后面很多内容都会出现，因为这是一个非常强大的中文宏包，简单来说就是专为中文文档准备的。

![就是你啦](https://th.bing.com/th/id/R.8a2ff8e33acbf0272c1050066e2b6323?rik=7d96yF4tBPzOsA&riu=http%3a%2f%2fimg2.biaoqingjia.com%2fbiaoqing%2f201607%2fd7d18683d621fbca464ca0815d2ce109.gif&ehk=o7PXeMI00Qnp4Q50%2fumUBAmFD5O6RJsHS9zlYCHTFqU%3d&risl=&pid=ImgRaw&r=0 "就是你啦")

### 导言区

为了便于观看，我们先上图

![code_2](https://pic4.58cdn.com.cn/nowater/webim/big/n_v2ebd40cd983bf40c380b0404f29d98aa2.png "code_2")

可以简单一眼就能看见，这里出现了一堆的 '\usepackage{xxxx}' 没错，这个所谓的usepackage就是LaTeX中我认为最强大的“宏包”命令，你只需要在导言区中引入宏包以后，然后经过一番操作的设置，就能简单获得自己想要的版面，设置的话，一般长下面这样：

![code_3](https://pic6.58cdn.com.cn/nowater/webim/big/n_v293703c574df2443f80f9854839fff0e1.png "code_3")

嗯嗯，不用看懂，记住大概就长这样就行了，

而如果正经地说导言区的作用的话，可以总结为以下几点

>1|| 文档类声明：用于指定文档类型，例如 \documentclass{article} 表示这是一篇文章。
>
>2|| 宏包引入：用于导入需要用到的宏包，例如 \usepackage{graphicx} 表示引入了图形处理宏包，从而可以插入图片到文档中。
>
>3|| 页面设置：用于设置文档的页面大小、页边距等，例如 \usepackage[a4paper, margin=2cm]{geometry} 表示将页面设置为 A4 大小，页边距为 2 厘米。
>
>4|| 字体设置：用于设置文档的字体样式和大小，例如 \usepackage{fontspec}\setmainfont{Times New Roman} 表示使用 Times New Roman 字体作为文档的主要字体。
>
>5|| 命令定义：用于自定义命令，例如 \newcommand{\mycmd}{\textbf{My command}} 表示定义了一个新命令 \mycmd，该命令将文本加粗并输出“My command”。
>
>6|| 元信息设置：用于设置文档的元信息，例如作者、标题、日期等，例如：
>
>>'''
>>\title{My title}
>>\author{My name}
>>\date{\today}
>>'''
>>
>>表示设置了文档的标题为“My title”，作者为“My name”，日期为当天日期。

而导言区中经常出现这么一个命令，就是 '\usepackage{xxxxxx}'

上面也提过了，这就是引入宏包，而宏包究竟是啥，下面会展开说说

### 正文

正文，字面意思啦，就是你写什么就是什么了，但是正文一般也可以有一些微妙的排版改变，这些在后面会展开

而且需要记住的一点就是，正文一般是以 '\begin{documentclass}'开始以'\end{documentclass}'结束的。

除了上面说到的三个结构外，其实LaTeX的文档结构也可以像下面这样分

>文档类声明：用于指定文档的类型，通常使用 \documentclass 命令来声明，例如 \documentclass{article} 表示这是一篇文章。
>
>导言区：位于文档类声明和 \begin{document} 命令之间的部分，用于引入宏包、定义命令、设置页面格式等，以及提供文档的元信息，如作者、标题、日期等。
>
>正文部分：位于 \begin{document} 和 \end{document} 命令之间的部分，用于编写文档的正文内容，包括段落、章节、列表、表格、公式等。
>
>参考文献：如果需要在文档中引用参考文献，可以使用 BibTeX 工具生成参考文献数据库文件，然后在文档中使用 \bibliography 命令和 \bibliographystyle 命令引用该数据库文件并设置参>考文献格式。
>
>附录部分：如果需要在文档中添加附录，可以使用 \appendix 命令声明附录部分，然后在该命令之后添加附录内容。
>
>结尾部分：位于 \end{document} 命令之后的部分，通常用于添加一些结尾语、致谢、声明等。

## 宏包（package）的个人理解

首先，宏包的概念我们可以直接百度一下：

>LaTeX 宏包是一组提供了一系列命令和宏定义的文件集合，用于扩展 LaTeX 的功能。它们可以被看作是一个功能库，类似于程序中的库文件，用于实现各种排版和格式的定制。
>
>通常，LaTeX 宏包由多个文件组成，其中一个主要的 .sty 文件定义了宏包的名称、版本、功能等信息，并包含了一系列的命令和宏定义。此外，宏包还可能包含一些 .cls 文件，用于定义文档类，以及一些 .tex 文件，用于提供示例文档、文档模板等。
>
>LaTeX 宏包可以从多个渠道获取，例如 CTAN（Comprehensive TeX Archive Network）网站提供了大量的宏包供用户下载和使用。用户可以根据自己的需求选择相应的宏包，并将其放置在 LaTeX 可以找到的位置。一旦载入了宏包，用户就可以使用其中定义的命令和宏了。
>
>总之，LaTeX 宏包可以帮助用户扩展 LaTeX 的功能，实现各种文档排版的需求，并使得用户可以快速地定制和创建符合自己需要的文档类和排版格式。

根据百度的内容，我们口语化的概括就是，宏包是在LaTeX中一个功能强大的工具，我们再举一个通俗的例子就是：

我们准备要拧螺丝，而这个螺丝是个“杯头内六角螺丝”（**就是我们的需求**）杯头内六角长下面这样

![内六角](https://www.google.com.hk/url?sa=i&url=http%3A%2F%2Fwww.hengtaiwj.com%2Fproduct%2F299.html&psig=AOvVaw1mFaLpcADBmmvmmxpjkjaF&ust=1678329131845000&source=images&cd=vfe&ved=0CA0QjRxqFwoTCKirj7Kly_0CFQAAAAAdAAAAABAD "内六角")

那很显然，我们就不能用“十字螺丝刀”了吧，那这时就要拿出内六角扳手（**就是我们需要的宏包**）才能拧这颗螺丝，那概括一下就是

宏包的作用就是为了达成我们对文档的**排版要求**而需要引入的**工具**

## 如何快速学习一个宏包的使用方法

而在LaTeX中宏包的数量不计其数，那这么多宏包不可能全部都学嘛，都是要用哪个放哪个，那这些需要使用到的宏包该去哪里找资料呢？这个其实也很简单，还记得在上篇文章中我们知道了怎么下载LaTeX的编译器**TeXLive**那它里面就会自动集成了一堆的宏包使用文档，我们称为**texdoc**

我们在学习相应的宏包的时候只要去找这些**texdoc**就能完全的了解这个宏包的用法，不用担心这些文档的专业性，这些文档就类似于开发者给出的技术手册，都是非常详细的。

而怎么找到这些**texdoc**只要打开我们电脑的cmd，输入'texdoc (package name)'就行,具体操作方法大家也可以看看下图

![TEXDOC](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExYTRmZjJjOTNhNzVlOGM1YjAyZTRlZGFjMjM4YmVmNjRlNzlhOTUyNSZjdD1n/rQrWcp5l0CN6bOJ8zC/giphy.gif "texdoc")

用文字去说明就是：

>首先，按住你键盘的**Win+R**键，输入**cmd**
>
>然后在cmd中输入**texdoc+你想要找的包的名称**
>>我这里找了一个数学公式包**amsth**

然后就会有一份PDF弹出来啦，这份就是手册，开始愉快学习吧

## 参考文献

>[LaTeX--5--一个文档的基本结构/导言区/标题_作者_日期](https://blog.csdn.net/Raging__Fire/article/details/115019928)
>><https://blog.csdn.net/Raging__Fire/article/details/115019928>
-----
>[LaTeX 宏包（\usepackage)](https://blog.csdn.net/qq_37556330/article/details/106190148)
>><https://blog.csdn.net/qq_37556330/article/details/106190148>
-----
>[使用texdoc命令查看tex宏包文档](https://www.latexstudio.net/archives/11243.html)
>><https://www.latexstudio.net/archives/11243.html>
-----

-----

大家也可以移步以下平台阅览本专栏，感谢

>微信公众号 **Jinyu Li OwO**

![推文QRcode.png](http://tva1.sinaimg.cn/large/008jd0Lugy1hbmks0or3xj30ev048750.jpg)

>[B站专栏](https://www.bilibili.com/read/readlist/rl678929?spm_id_from=333.999.0.0)
>><https://www.bilibili.com/read/readlist/rl678929?spm_id_from=333.999.0.0>
> -----
>[知乎](https://www.zhihu.com/column/c_1611528726348275712)
>><https://www.zhihu.com/column/c_1611528726348275712>
> -----
>[CSDN](https://blog.csdn.net/ljy025/category_12214744.html)
>><https://blog.csdn.net/ljy025/category_12214744.html>

公众号更新
>周三（11：45） 周六（16：30）

其他平台不定期。
