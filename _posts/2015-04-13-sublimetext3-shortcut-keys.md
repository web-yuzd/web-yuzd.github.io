---
layout: post
title: "sublimetext3常用快捷键"
description: "sublimetext3常用快捷键"
category: ['work', 'code']
tags: ['技巧']
---
{% include JB/setup %}

Sublime Text 3也用了一段时间了，但是想要用好，一些快捷键不可或缺，太多也记不住的，所以在网上搜集了一些常用快捷键和实用功能，在忘记的时候方便查看。下面是Windows系统下常用快捷键：

# 快捷键汇总

## 选择类
**Ctrl+D** 选中光标所占的文本，继续操作则会选中下一个相同的文本。

**Alt+F3** 选中文本按下快捷键，即可一次性选择全部的相同文本进行同时编辑。举个栗子：快速选中并更改所有相同的变量名、函数名等。

**Ctrl+L** 选中整行，继续操作则继续选择下一行，效果和 Shift+↓ 效果一样。

**Ctrl+Shift+L** 先选中多行，再按下快捷键，会在每行行尾插入光标，即可同时编辑这些行。

**Ctrl+Shift+M** 选择括号内的内容（继续选择父括号）。举个栗子：快速选中删除函数中的代码，重写函数体代码或重写括号内里的内容。

**Ctrl+M** 光标移动至括号内结束或开始的位置。

**Ctrl+Enter** 在下一行插入新行。举个栗子：即使光标不在行尾，也能快速向下插入一行。

**Ctrl+Shift+Enter** 在上一行插入新行。举个栗子：即使光标不在行首，也能快速向上插入一行。

**Ctrl+Shift+[** 选中代码，按下快捷键，折叠代码。

**Ctrl+Shift+]** 选中代码，按下快捷键，展开代码。

**Ctrl+K+0** 展开所有折叠代码。

**Ctrl+←** 向左单位性地移动光标，快速移动光标。

**Ctrl+→** 向右单位性地移动光标，快速移动光标。

**shift+↑** 向上选中多行。

**shift+↓** 向下选中多行。

**Shift+←** 向左选中文本。

**Shift+→** 向右选中文本。

**Ctrl+Shift+←** 向左单位性地选中文本。

**Ctrl+Shift+→** 向右单位性地选中文本。

**Ctrl+Shift+↑** 将光标所在行和上一行代码互换（将光标所在行插入到上一行之前）。

**Ctrl+Shift+↓** 将光标所在行和下一行代码互换（将光标所在行插入到下一行之后）。

**Ctrl+Alt+↑** 向上添加多行光标，可同时编辑多行。

**Ctrl+Alt+↓** 向下添加多行光标，可同时编辑多行。


## 编辑类

**Ctrl+J** 合并选中的多行代码为一行。举个栗子：将多行格式的CSS属性合并为一行。

**Ctrl+Shift+D**  复制光标所在整行，插入到下一行。
Tab 向右缩进。

**Shift+Tab** 向左缩进。

**Ctrl+K+K** 从光标处开始删除代码至行尾。

**Ctrl+Shift+K** 删除整行。

**Ctrl+/** 注释单行。

**Ctrl+Shift+/** 注释多行。

**Ctrl+K+U** 转换大写。

**Ctrl+K+L** 转换小写。

**Ctrl+Z** 撤销。

**Ctrl+Y** 恢复撤销。

**Ctrl+U** 软撤销，感觉和 Gtrl+Z 一样。

**Ctrl+F2** 设置书签

**Ctrl+T** 左右字母互换。

**F6** 单词检测拼写


## 搜索类

**Ctrl+F** 打开底部搜索框，查找关键字。

**Ctrl+shift+F** 在文件夹内查找，与普通编辑器不同的地方是sublime允许添加多个文件夹进行查找，略高端，未研究。

**Ctrl+P** 打开搜索框。举个栗子：1、输入当前项目中的文件名，快速搜索文件，2、输入@和关键字，查找文件中函数名，3、输入：和数字，跳转到文件中该行代码，4、输入#和关键字，查找变量名。

**Ctrl+G** 打开搜索框，自动带：，输入数字跳转到该行代码。举个栗子：在页面代码比较长的文件中快速定位。

**Ctrl+R** 打开搜索框，自动带@，输入关键字，查找文件中的函数名。举个栗子：在函数较多的页面快速查找某个函数。

**Ctrl+：** 打开搜索框，自动带#，输入关键字，查找文件中的变量名、属性名等。

**Ctrl+Shift+P** 打开命令框。场景栗子：打开命名框，输入关键字，调用sublime text或插件的功能，例如使用package安装插件。

**Esc** 退出光标多行选择，退出搜索框，命令框等。


##显示类

**Ctrl+Tab** 按文件浏览过的顺序，切换当前窗口的标签页。

**Ctrl+PageDown** 向左切换当前窗口的标签页。

**Ctrl+PageUp** 向右切换当前窗口的标签页。

**Alt+Shift+1** 窗口分屏，恢复默认1屏（非小键盘的数字）

**Alt+Shift+2** 左右分屏-2列

**Alt+Shift+3** 左右分屏-3列

**Alt+Shift+4** 左右分屏-4列

**Alt+Shift+5** 等分4屏

**Alt+Shift+8** 垂直分屏-2屏

**Alt+Shift+9** 垂直分屏-3屏

**Ctrl+K+B** 开启/关闭侧边栏。

**F11** 全屏模式

**Shift+F11** 免打扰模式

#常用功能

### 1. Goto Anything功能 — 快速查找（ctrl + P）
输入@+函数名可以快速找到函数。
输入#+文本可以快速进行文件内文本匹配。

### 2. 多行游标功能（ctrl + D，非常实用）
如何将文件中的某个单词更改为另一个？
方法一：利用查找替换功能：ctrl + H
方法二（推荐）：多行游标功能，选中一个后，按ctrl+D可以同时选中另一个，同时多了另一个光标。

### 3. 命令模式（应尽可能使用，而不用浪费脑细胞记忆大量命令的快捷键）
比如用ctrl+N新建一个文件后，默认是plain text，没有语法高亮功能，如何设置语法模式？
- 可以通过右下角的语法选择区选择希望设置的语法模式。
- 还有另一种更好的办法，即使用ctrl + shift + P打开命令模式，然后输入set syntax [language]设置为某种语言的语法模式，比如set syntax java则设置为java语法高亮。
- st3支持模糊匹配，你也可以直接输入syntax java或ssjava。
- 若当前已经是某种语言的语法模式，则可以直接输入其它语言进行切换（而不用输入set syntax或syntax了），比如当然为java语法模式，那么直接输入js就可以马上切换为javascript语法模式。

还可以输入minimap隐藏或显示右边的minimap缩影


### 4. 快速跳转到某一行
按下Ctrl + G，输入行号，可以快速跳转到该行。


### 5. 快速添加新行
Ctrl + Enter可以在当前行下新建一行。
Ctrl + Shift + Enter可以在当前行上面添加一行。

### 6. 多行缩进
选中多行后按Ctrl + ]可以增加缩进，按Ctrl + [可以减少缩进。
PS：发现用Tab和Shift + Tab也是可以的。


### 7. 完整拷贝，避免格式错乱
我们发现，在从别的文件中拷贝一段代码过来的时候，多半只是第一行缩进，后面都乱了，这时可以使用Ctrl + Shift + V进行粘贴，可以在粘贴的过程中保持缩进，这时格式都是正确的。


### 8. 重新打开关闭的标签
在Chrome里面，如果你不小心关闭了某个标签页并想恢复它，你可以按下Shift + Ctrl + T重新打开它。
在ST3中也一样，如果你不小心关闭了某个文件，可以按下Shift + Ctrl + T快速恢复。连续重复该按键，ST将会按照关闭的先后顺序重新打开标签页。


### 9. 按住shift + ctrl然后按←或→可快速选中一行中的某一部分，连续按扩大选择范围。
比如你需要将某一部分进行注释(ctrl+/)或删除，使用这个功能就很方便。


### 10. 上下移动行
定位光标或选中某块区域，然后按shift+ctrl+↑↓可以上下移动该行。


### 11. shift + ctrl + d可快速复制光标所在的一整行，并复制到该行之前。

### 12. Ctrl+Shift+M：选中花括号里面的全部内容不包括{}。

### 13. Ctrl+Shift+K：删除整行。

### 14. 快速关闭HTML里的标签

写html文件时利用快捷键Alt + .可以快速关闭某个标签，如写<html>后按Alt+.可以快速得到</html>。
但这样还是挺繁琐，可以使用前端插件Emmet插件，直接在新建的html文件里（首先得设置语法模式为html）直接输入!（代表html5格式的html文档）然后按下ctrl+E即可。
