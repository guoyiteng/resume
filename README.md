# 一个简洁优雅的 XeLaTeX 简历模板

Hit branch [zh_CN](https://github.com/billryan/resume/tree/zh_CN) if you want a Simplified Chinese résumé.

每年的9月10月是求职的高峰季，除了简历上充实的干货之外，一份美美的简历自然是能助你一臂之力的啦。

\LaTeX 的简历模板其实是有不少的，坊间流传较广的有 `moderncv`, 这货使用起来比较简单，样式改起来也很方便，但是不太适合作为一页纸简历模板，因为空白太多了。传统的 `resume` 宏包虽然适合用作一页纸简历，但是定制起来比较麻烦，需要懂不少 \TeX 语法。看过不少模板，老是觉得有什么地方不满意(处女座改变世界...)，思来想去俺就自己从 ShareLaTeX 网站上找了个极简教程自己鼓捣了一个还算优雅的简历模板出来。

受以下项目启发：

- [zachscrivena/simple-resume-cv](https://github.com/zachscrivena/simple-resume-cv)
- [res](https://www.ctan.org/pkg/res)
- [JianXu's CV](http://www.jianxu.net/en/files/JianXu_CV.pdf)
- [Web Front-End Wenli Zhang.pdf](http://zhangwenli.com/cv/Web%20Front-End%20Wenli%20Zhang.pdf)
- [paciorek's CV/Resume template](http://www.stat.berkeley.edu/~paciorek/computingTips/Latex_template_creating_CV_.html)
- [How to write a LaTeX class file and design your own CV (Part 1) - ShareLaTeX](https://www.sharelatex.com/blog/2011/03/27/how-to-write-a-latex-class-file-and-design-your-own-cv.html)

其中最后一条 shareLaTeX 的总结清晰易懂，强烈建议围观。接下来介绍模板使用细节和定制说明。

## 简介

该简历模板使用 \XeLaTeX 编译，无痛支持中文，开箱即用(几乎不需要懂 \LaTeX 语法)，除了本地编译外也可使用 Sharelatex **在线编译**，无需在本机安装 TeX 发行版。

- Easy to further customize or extend
- Full support for unicode characters (e.g. CJK) with \XeLaTeX\
- Perfect Simplified Chinese fonts supported with Adobefonts
- FontAwesome 4.6.3 support

## Quick Start
- Fork this repository
- Add information about you directly in GitHub
- Compile TeX file to PDF with [LaTeX.Online](https://latexonline.cc/)

- 极其容易定制和扩展。
- 完善的 Unicode 字体支持，因为用的是 XeLaTeX 嘛
- 完美的简体中文支持，默认使用 adobefonts 的四套简体中文字型，其他字型可自行添加。
- 支持图标字体 FontAwesome 4.6.3

### 样例输出

- [PDF, English](https://latexonline.cc/compile?git=https://github.com/billryan/resume&target=resume.tex&command=xelatex)
- [PDF with the photo, English](https://latexonline.cc/compile?git=https://github.com/billryan/resume&target=resume_photo.tex&command=xelatex)
- [简体中文 PDF](http://7xojrx.com1.z0.glb.clouddn.com/docs/resume-zh_CN.pdf)

![English](http://7xojrx.com1.z0.glb.clouddn.com/docs/resume.png)
![English with photo](http://7xojrx.com1.z0.glb.clouddn.com/docs/resume_photo.png)
![简体中文](http://7xojrx.com1.z0.glb.clouddn.com/docs/resume-zh_CN.png)

## Usage

英文模板范例见 <https://github.com/billryan/resume/blob/zh_CN/resume.tex> 
中文模板范例见 <https://github.com/billryan/resume/blob/zh_CN/resume-zh_CN.tex>

If you only need a résumé in English or have installed Adobe Simplified Chinese on your OS, **It would be better to clone only the master branch,** since the Simplified Chinese fonts files are too large.

```
\usepackage{zh_CN-Adobefonts_external} % Simplified Chinese Support using external fonts (./fonts/zh_CN-Adobe/)
%\usepackage{zh_CN-Adobefonts_internal} % Simplified Chinese Support using system fonts
\usepackage{linespacing_fix} % disable extra space before next section
```

对于高级用户：如果系统已确定安装有 Adobe 的四套中文字型，在文档的开始处使用包`zh_CN-Adobefonts_internal`，这样第一次编译时也会很快。

### 参考文献

参考文献的引用采用 bib + bst 的方式管理，bib 中存放 BibTeX 格式的引用文本，bst 用于控制 bib 文件的展示形式，默认为 IEEEtran. 编译方式可选如下：

1. OSX/Linux 用户 `latexmk -pdf -pvc -silent myresume-zh_CN.tex` latexmkrc 配置文件可参考我的 [dotfiles/latexmkrc](https://github.com/billryan/dotfiles/blob/master/latex/latexmkrc)
2. Windows 用户可使用 WinEdt 中的 TeXify 选项编译(未测试)

除了以上两种编译方式，你还可以使用传统的编译方式：

```shell
xelatex myresume-zh_CN
bibtex myresume-zh_CN
xelatex myresume-zh_CN
xelatex myresume-zh_CN
```

范例文档中默认Reference 另起一页，想留在当前页的可注释掉`\newpage`

### 宏

普通用户直接使用模板中的宏即可，具体排版使用可直接参考范例 tex 文档，已经十分简洁了。
想自己添加新的宏的可以先看看 [How to write a LaTeX class file and design your own CV (Part 1) - ShareLaTeX](https://www.sharelatex.com/blog/2011/03/27/how-to-write-a-latex-class-file-and-design-your-own-cv.html) 和 [How to write a LaTeX class file and design your own CV (Part 2) - ShareLaTeX](https://www.sharelatex.com/blog/2013/06/28/how-to-write-a-latex-class-file-and-design-your-own-cv.html) 了解下该模板的简单背景。

- `\name`: 姓名
- `\email`: 邮箱
- `\linkedin`: LinkedIn
- `\basicInfo`: 联系信息, 按需加入
- `\section`: 用于分节, 如教育背景, 实习/项目经历等
- `\subsection`: 用于小节标题, 无日期选项
- `\datedsubsection`: 用于小节标题, 简历中使用最广，第二项为时间区间，自动右对齐
- `\itemize`: 清单列表，简历中应用最广
- `\enumerate`: 枚举列表，数字标号

### FontAwesome

首先在 [Font Awesome Icons](http://fortawesome.github.io/Font-Awesome/icons/) 上选中自己想使用的图标，然后在 [fontawesome.sty](https://github.com/billryan/resume/blob/zh_CN/fontawesome.sty) 中找到相应的宏, 将其作为普通文本一样使用。
如果不需要使用 FontAwesome 字体的把那些宏去掉即可。
其他的可以自行参考相应 cls 和 tex 文件。

## License

[The MIT License (MIT)](http://opensource.org/licenses/MIT)

Copyrighted fonts are not subjected to this License.

## 总结

\LaTeX 的中文支持除了在系统配置文件内指定外还可以在当前项目内指定，这种方式适合大范围分发，正是这个模板中采用的方式，缺点就是大部分中文字型都是有版权的，使用上需要注意。在制作这个模板的过程中还发现合理使用 \LaTeX 现代宏包能大大减轻后期维护和升级的工作，需要使用的命令更少更清晰。ShareLaTeX 网站上有很多简单易懂的范例，当教材来使都不过分。\LaTeX 中文方面的教程精品的不多，刘海洋老师的《LaTeX 入门》 算是精品中的精品！

这个模板看似复杂，其实使用上极其省心，想在我这个模板的基础上改动样式的可以看相应的 cls 文件和详细说明，只是简单使用的话直接在范例文档的基础上改改即可。
总的来说这个模板适合找工作用，而且是偏技术型的一页纸简历。

祝大家玩的开心 :)
