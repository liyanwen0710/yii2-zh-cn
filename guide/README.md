必读 之 翻译流程Translation workflow
====================

为了方便大家更好的了解指南手册的翻译项目，这里特地为大家提供翻译的相关流程的相关讲解。

通识General
------------------

###其一，我们的工具
工欲善其事，必先利其器。在翻译的过程，我们默认采用Transifex等专业的翻译工具来进行，
可以简化翻译流程，提高翻译的速度和质量，降低审阅的困难度。但是，请大家依照规范进行命名和组织，
尽量避免重复劳动。详细的讲解请参阅Transifex部分。

###其二，术语表
关于某些特定概念，我们应该遵循相同的术语翻译，有些Yii的独有概念，其含义也很好理解的，我们选择不翻译。
相关术语的介绍和参考翻译请见[官方的术语表](glossary.md)以及Transifex上[我们Project的术语表](#%E6%9C%AF%E8%AF%AD%E8%A1%A8)。
###其三，翻译与校阅
翻译的内容是繁重的，然而校阅的工作也是重要的。

Transifex
------------------
###使用的基本流程###
[登陆](https://www.transifex.com/signin/?next=/projects/p/yii2-guide-chinesization-program/)后，
打开组织，点选项目，选择中文语言（代码``zh_CN``），选择想要翻译的资源（文件），开始翻译字符串。
（注：前两项可以简化为用[t.yii2.cn](http://t.yii2.cn)直接访问）

###翻译小循环###
进入具体翻译的页面，这里以[ActiveRecord](https://www.transifex.com/projects/p/yii2-guide-chinesization-program/translate/#zh_CN/active-record)为例。

####复制文本
长句子，可以点击右上角机器翻译。（注：机翻使用的是qiansen1386同学搭建的Microsoft的在线翻译API，Google的收费，而Microsoft的有免费限额，每月刷新。
简单的句子能不机翻就不要机翻，月末如果机翻功能还能用，就赶紧用，多多地用，够本地用。）
短句子直接点复制原文。

####翻译
额，就翻译啊。

查有道，查Google，参考[Yii1.1的手册翻译](http://www.yiiframework.com/doc/guide/1.1/zh_cn/index)。可能有些文字，涉及较深的专业知识，其含义本身就算是中文也不太好理解。你可以选择跳过，也可以选择查阅相关维基百科，来搞明白这些概念，方便的话请随后把这些概念加入[术语表](#%E6%9C%AF%E8%AF%AD%E8%A1%A8)。

####术语表
值得注意的一点是，如果有相应的词条被加入了**[词汇表（术语表，或者叫Glossary）](https://www.transifex.com/projects/p/yii2-guide-chinesization-program/glossary/l/zh_CN/)**
就可以在上面的原文中，用鼠标指向相关词条，参考其相关的术语译名的提示。同时在最下部的面板的词汇表选项卡中还会有其详细的介绍和相关讨论。
如果在翻译的过程中，发现有新的术语，然而它还没有被加入术语表，请千万帮忙加入，防止同一个术语在不同字符串里的翻译不同，这很重要。
同时一个术语的翻译可能影响其他所有人的翻译，请添加术语之前一定要查阅下Yii1.0时代的翻译，确保传承性。如果有术语翻译错误的地方，还请改正或讨论。
PS：目前我不知道添加术语是否需要权限，如果需要请在群里说下，请东方（也就是qiansen1386）帮大家提权。

###不应翻译的字符串

有些字符串是不应该被翻译的，比如：

1.源代码。注：源代码我们不翻译，但是注释还是要翻译的，别漏了。
2.众所周知的概念，如ActiveRecord，Alias，AssetManager，这类概念仅在标题处注释其中文名称即可，具体翻译中最好不要
使用其中文名称，原因有二，其一，这些是Yii的独有概念，其在语境中的含义和在其他编程语言中不一定相同。比如AR在Yii中是其独特封装的ORM，
其实现和理念与在Ruby中并不尽相同。其二，为了国际化的需要，由于工作量的原因，我们不太可能翻译世界上出现的每一篇有关Yii的教程和心得分享。
所以看懂原文就显得比较重要，而这些概念在有道和Google上翻译的都是英文领域的概念，而非Yii语境下的概念，帮助大家对其英文原词建立相应
的概念就显得非常重要。
3.Markdown语法。transifex没有Markdown识别，有些markdown语法会被识别为字符串。
比如：``------------------``。关于Markdown这一块，在下面的字符串排序段落还会说到。

如果发现这类字符串，就点击复制原文，然后点保存，接着点审核，之后该字符串在文件中的所有重复出现的身影就都被忽略掉了。

###字符串的排列顺序###

字符串的排列顺序，基本等同于原文顺序，但是又少许不同需要特别注意。
其一，已经出现的字符串不会再次出现，也就是不会出现重复翻译的情况。
比如
```Markdown
    /**
```
这条字符串不会再次出现，有可能会给内容类型的判断造成困扰，这点也是Transifex不完善的地方。

第二，由于transifex没有Markdown识别，所以所有的文本都是以Plain Text的类型进行识别的，所以当原句中出现``[[这种连接]]``的
之后，断句可能会出现错误。大家翻译的时候，不要太过信任机翻需要联系上下文啊。那么，中文翻译应该放在哪里呢，请见下条。

###字符串的断句###
我们需要把这句话的中文翻译放置在这句话的主要部分存在的字符串中，至于遗留在其他地方的碎片，大家不要理会就好，因为我到现在为止没有发现可以灵活调整transifex字符串断句的方法，或许就没有。



翻译Translator
------------------

待定...

校阅Reviewer
------------------

待定...