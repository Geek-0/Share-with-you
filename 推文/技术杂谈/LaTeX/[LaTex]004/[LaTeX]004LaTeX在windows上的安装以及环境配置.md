  [//]: // (作者：JinyuLi)
  [//]: // (日期：2023.03.03)
  [//]: // (内容：[LaTeX]004LaTeX在windows上的安装以及环境配置)

# LaTeX分享【LaTeX在windows上的安装以及环境配置】

>作者：JinyuLi
>
>日期：2023.03.03
>
>内容：LaTeX在windows上的安装以及环境配置
>>1、LaTeX编写及编译环境的简介
>>
>>2、配置教程推荐（非原创部分，请勿误解）
>>
>>3、一些LaTeX学习网站、BLOG、文档的推荐（主要说说怎么快速查找宏包（package）使用手册）

本文观前提醒：*文章**配置部分**内容是直接推荐的网络文章，并非原创，网页链接直接附在该文文末，请大家自行点击阅览*

## LaTeX编写及编译环境的简介

在我前面写过的关于**[LaTeX的介绍](https://zhuanlan.zhihu.com/p/609342567)**一文中，就曾说过

>LaTeX 是一种基于 TeX 的排版系统，它使用的是一种类似于程序的语言，即 LaTeX 源代码，而不是直接书写最终的文档内容。

具体的LaTeX源文件的内容大概长下面这样：

![源文件视觉样式](http://tva1.sinaimg.cn/large/008jd0Lugy1hbn5us3kz8j316z0ovqfx.jpg)

很容易就能看出，这就是类似于代码的一份源文件，所以，既然LaTeX是一种类似程序的语言，那么说到运行程序，那么很自然的就能联想到程序在正式运行前，还需要经过最重要的一步，那就是**编译**，那么需要对程序进行编译，那么我们自然就需要一些编译工具，在了解有什么编译的工具之前，我更想和大家分享一下，LaTeX编译的这个过程发生了什么，又会产生些什么文件，以及这些文件的作用。

### LaTeX编译过程简介

首先，下面是一个LaTeX源文件从单纯的文本，代码编译之后生成一份PDF电子文档的一个大概的过程

![编译流程简图](http://tva1.sinaimg.cn/large/008jd0Lugy1hbn5us2rg4j30nj0adtbz.jpg)

从这个图中，我们可以把LaTeX的编译过程简单的划分为三个部分

>将 LaTeX 源代码转换为 TeX 源代码：LaTeX 源代码中包含了一些命令和宏定义，需要先将其转换为 TeX 语言的源代码，才能进行后续处理。
>
>运行 TeX 引擎进行排版：TeX 引擎是一种排版引擎，它将 TeX 源代码转换为 DVI（设备无关文件）格式的文件，包括字体选择、页面布局、断词等操作。
>>注：图片中的LaTeX引擎就是指TeX引擎，只要理解为同一东西就好，再深究的我也不懂[Doge]
>
>将 DVI 文件转换为最终的文档格式：根据需要生成 PDF、PS 等格式的文件，需要使用一些工具和程序进行转换和处理。
>>在这里，生成的PDF文件需要使用PDF阅读器进行再一步的阅览

而LaTeX需要编译才能使用，个人认为这种略显麻烦的操作也带来了一种优点，因为美编译一次都会产生一份PDF，而且在每次编译的过程，还会产生一份编译每个版本的时候会有什么变化的，log文件进行记录，那么这就极大的方便了我们去做版本的迭代和管理，也更容易溯源，这会在多人协作编撰文档中起到一些让大家都连连称赞的作用。

### LaTeX编译产生文件及作用

在LaTeX编译的过程中除了源文件.tex文件，以及生成的.pdf文件之外，还会产生下面这些文件

.tex 文件：LaTeX 源文件，包含文档的内容和格式。

.aux 文件：辅助文件，记录了交叉引用、目录、参考文献等信息，用于下一次编译。

.log 文件：编译日志文件，记录了编译过程中的各种信息，包括错误、警告、页面布局等。

.toc 文件：目录文件，记录了文档的章节、节、子节等结构，用于生成目录。

.lof 文件：图形列表文件，记录了文档中使用的图形的信息，用于生成图形列表。

.lot 文件：表格列表文件，记录了文档中使用的表格的信息，用于生成表格列表。

.bbl 文件：参考文献文件，记录了文档中使用的参考文献的信息，用于生成参考文献列表。

.blg 文件：参考文献编译日志文件，记录了参考文献的编译过程中的各种信息。

.pdf 文件：最终生成的文档文件，可以直接打印或者阅读。

其中一头一尾的.tex .pdf外，其他的文件都是编译过程中的辅助文件，可以根据需要进行处理或删除。这些文件的作用包括记录文档的结构、内容、格式、引用、参考文献等信息，方便后续的编译、修改、格式调整等操作。

这里要说明一下后面可能会介绍到的另一种格式的文件 .bib 文件，这个文件最主要的作用是在写论文的时候要用到，是用来管理引用文献或者链接等引用的管理文件。

### LaTeX编译工具推荐

这里，我直接给出一篇参考BLOG供大家阅读，大家可以点击链接进行观看：

[博文推荐](https://blog.csdn.net/xueshengke/article/details/52883064) <https://blog.csdn.net/xueshengke/article/details/52883064>

其中我个人比较推荐 Overleaf 的使用，但是这个工具可能使用科学上网的方法用起来会比较顺畅，但是我认为它强的点就在于，它是云端储存，而且不用下载臃肿的编译器，直接网页编撰就行，更好的一点就一定是适用于团队工作的特性了，毕竟现在的云端软件多少都沾点社交或者说群体属性，几乎都已经成为一种潮流了。

而另外一种我也推荐并正在使用的就是 LaTeX+VScode 的组合配方，我个人觉得使用起来很顺手，下面的配置教程也给出了配置教程，大家可以自行前往观看。

## 配置教程推荐

这里给出常用的系统的LaTeX的配置以及初步使用方法，大家可以选择观看

[Windows系统下LaTeX+VScode的配置](https://zhuanlan.zhihu.com/p/166523064) <https://zhuanlan.zhihu.com/p/166523064>

[Ubuntu系统下LaTeX配置方法](https://zhuanlan.zhihu.com/p/65931654) <https://zhuanlan.zhihu.com/p/65931654>

[Mac系统的LaTeX配置](https://zhuanlan.zhihu.com/p/440869635) <https://zhuanlan.zhihu.com/p/440869635>

这里还要给出一个**免责声明**

1、 教程我只试过第一二个，并且都获得成功才推荐的，因为我没有Mac设备，所以没有尝试过Mac是否能和教程一样可行

2、 我的系统可行并不代表读者你的可行，如果遇到什么BUG我可能也没遇到过

3、 以上教程均来源网络，我只是和大家分享

## 参考文章链接

[Windows系统下LaTeX+VScode的配置](https://zhuanlan.zhihu.com/p/166523064) <https://zhuanlan.zhihu.com/p/166523064>

[Ubuntu系统下LaTeX配置方法](https://zhuanlan.zhihu.com/p/65931654) <https://zhuanlan.zhihu.com/p/65931654>

[Mac系统的LaTeX配置](https://zhuanlan.zhihu.com/p/440869635) <https://zhuanlan.zhihu.com/p/440869635>

[LaTeX编译工具推荐](https://blog.csdn.net/xueshengke/article/details/52883064) <https://blog.csdn.net/xueshengke/article/details/52883064>

[LaTeX排版札记：Part 1—编译器的选择和安装](https://zhuanlan.zhihu.com/p/32280635) <https://zhuanlan.zhihu.com/p/32280635>

[论文写作利器---LaTeX教程（入门篇）（更新中）](https://blog.csdn.net/brave_stone/article/details/88913010) <https://blog.csdn.net/brave_stone/article/details/88913010>

## 后续预告

LaTeX从源文件到PDF的基本操作与资料查找方式。
**以上即为今日分享内容，祝各位周末愉快，我们周三见**

大家也可以移步以下平台阅览本专栏，感谢

>微信公众号 **Jinyu Li OwO**

![推文QRcode.png](http://tva1.sinaimg.cn/large/008jd0Lugy1hbmks0or3xj30ev048750.jpg)

>[B站专栏](https://www.bilibili.com/read/cv21970159)<https://www.bilibili.com/read/cv21970159>
>
>[知乎](https://www.zhihu.com/column/c_1611528726348275712)<https://www.zhihu.com/column/c_1611528726348275712>
>
>[CSDN](https://blog.csdn.net/ljy025/category_12214744.html)<https://blog.csdn.net/ljy025/category_12214744.html>

公众号更新
>周三（11：45） 周六（16：30）

其他平台不定期。
