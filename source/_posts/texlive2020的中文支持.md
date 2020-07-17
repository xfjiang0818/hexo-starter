---
title: texlive2020的中文支持
date: 2020-07-17 21:23:32
tags: LaTeX
categories:
mathjax: true
---

![avatar](https://cdn.jsdelivr.net/gh/xfjiang0818/pictures@2020.7.17/20200620.jpg)

<!-- more -->

## $\LaTeX$ 支持中文的宏包：CJK 和 CTEX

### CJK

宏包路径：texlive\2020\texmf-dist\tex\latex\cjk

从说明文档中截取编码相关部分

```
<encoding>      These character sets and encodings are currently
                implemented in CJK.enc:

                    Bg5  (For traditional Chinese. Mainly used in Taiwan.
                          Character set: Big 5.
                          Encoding: Big 5 without UDA2 and UDA3.)
                    Bg5+ (For traditional Chinese. Obsolete.
                          Character set: Big 5+.
                          Encoding: GBK.)

                    HK   (For traditional Chinese. Used in Hong Kong.
                          Character set: Big 5 + HKSCS-2004.
                          Encoding: Full Big 5.)

                    GB   (For simplified Chinese. Mainly used in
                          PR China. Also called `EUC-CN'.
                          Character set: GB 2312-1980.
                          Encoding: EUC.)
                    GBt  (For traditional Chinese. Rarely used in
                          PR China.
                          Character set: GB/T 12345-1990.
                          Encoding: EUC.)
                    GBK  (For Chinese. An extension of GB 2312.
                          Character set: GBK.
                          Encoding: GBK.)
                   	...
                    UTF8 (Unicode Transformation format 8, also called
                          `UTF-2' or `FSS-UTF'.
                          Character set: Unicode.
                          Encoding: UTF-8.)
```

可见 CJK 同时支持 GBK 和 UTF8

### CTEX

宏包路径：texlive\2020\texmf-dist\tex\latex\ctex

CTEX 支持 GBK 和 UTF-8

### 说明

（1）建议写新文档时使用 UTF-8 编码，GBK 仅留给历史遗留文档。

（2）CTEX 是一个支持汉字的宏包，不同于 Ctex 套装。后者包括了编辑器和大量的宏包，自带编辑器 WinEdt 的默认编码是 GB 2312。



## 三种方式支持 UTF-8 编码的中文

### 1. CJK 宏包的 UTF-8

texlive\2020\texmf-dist\tex\latex\cjk\texinput 目录下存在 UTF8 和 GB 两个目录，UTF8 目录下有字体文件。

使用方法

```latex
\usepackage(CJKutf8)
\begin{document}
\begin{CJK}{UTF8}
...
\end{CJK}
\end{document}
```

<font color=red>注：经过一次简单测试，使用“CJK”或者“CJKutf8”效果似乎一样</font>

### 2. CTEX 宏包的 UTF-8

使用方法有两种

```latex
\documentclass[UTF8]{article}
\usepackage(CTEX)
\begin{document}
...
\end{document}
```

或者使用 CTEX 标准类

```latex
\documentclass[UTF8]{ctexart}
\begin{document}
...
\end{document}
```

| LaTeX 标准文档类 | CTEX 文档类 |
| ---------------- | ----------- |
| article          | crexart     |
| report           | ctexrep     |
| book             | ctexbook    |
| beamer           | ctexbeamer  |

### 3. XeLaTex 编译

XeTeX 是使用 Unicode 的 Tex 排版引擎，默认输入文件是 utf-8 编码。XeTeX 可以在不进行额外配置的情况下，直接使用系统中安装的字体。XeLaTeX 是使用 LaTeX 的排版引擎，也有上述 XeTeX 的优点。

XeLaTeX 在 cmd 中可直接生成 pdf 文件XX

```
xelatex XXXX.tex
```

使用方法

```latex
\documentclass{article}
\usepackage{CTEX}
...
```

<font color=red>注：与原文章中的说明不同的是，在测试中 pdflatex 和 xelatex 都会成功，并且 pdflatex 的用时较短。</font>



## 参考：

[LaTex支持中文的三种方式](https://blog.csdn.net/z_feng12489/article/details/90449495 "LaTex支持中文的三种方式")

[Latex中文utf-8编码的三种方式](https://blog.csdn.net/q524369615/article/details/78254042 "Latex中文utf-8编码的三种方式")

以上两篇文章原创作者不详