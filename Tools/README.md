# Tools

趁手的工具对开发过程非常重要，本文档会列出开发中常用工具，并记录他们的使用方法及技巧。

## 集成开发环境

- MDK
- IAR
- Eclipse
- Pycharm

## 版本管理

- [Git 工具常用操作及技巧](../Gist/Git.md)
- 和 Git 配合使用的对比工具：[Beyond Compare](https://www.scootersoftware.com/download.php)，界面简洁，功能强大
- Linux 下好用的 GUI Git 工具 [GitKraken](https://www.gitkraken.com/) 

## 终端 shell

- 终端软件：[Xshell](http://www.netsarang.com/products/xsh_overview.html) 一个强大的安全终端模拟软件

## Python Library

- [JSON Schema](https://json-schema.org/understanding-json-schema/) and [JSON Schema generator](https://pypi.org/project/genson)

## 编辑器

### Pycharm

优秀的纯文本编辑器（当然也包括代码）非常重要，现在我使用 Pycharm 作为主力编辑器，下面列一下常用的编辑器快捷键:

| 功能 | 快捷键 |
| ------ | ------ |
| 删除当前行 | CTRL + D |
| 上下移动当前行| ALT + UP/DOWN |
| 向下拷贝当前行| CTRL + ALT + DOWN  |
| 移动到当前行首以及行末尾| HOME/END |
| 选中当前行或者多行| SHIFT + END/UP/DOWN  |
| 选中当前的单词/行| 鼠标点击两次/三次 |
| 选中当前行光标前半段和后半段| SHIFT + CTRL + LEFT/RIGHT  |
| 替换| CTRL + R |
| 全局替换| CTRL + SHIFT + R  |
| 全局查找| CTRL + SHIFT + F |
| 代码格式化| CTRL + ALT + L  |
| git commit| CTRL + K  |
| git commit + push| CTRL + ALT + K  |
| git push| SHIFT + CTRL + K  |

### MarkDown

- 非常好用的本地 MarkDown 编辑器：[Typora](https://www.typora.io/)，支持 md 格式向各种格式的轻松转换
- 云端 MarkDown 编辑器：[Cmd MarkDown](https://www.zybuluo.com/mdeditor)，云端保存和搜索功能十分强大

### VScode

#### 通过 bear 支持跳转

使用 bear 工具记录工程编译命令，然后添加到 vscode 的  Compile Commands 配置中，可以帮助编辑器优先跳转到预先指定路径的代码，无需手动添加头文件路径。

```
apt install bear
```

在 make 命令前添加：

```
bear make xxx
```

会在编译目录生成 `compile_commands.json` 文件，拷贝到根目录，在工作区添加该配置，只在工作区生效，编辑器就可以根据编译配置来跳转了。

![image-20230809104222731](figures/image-20230809104222731.png)

#### 屏蔽不需要的文件

在工程顶层目录中新建 `.vscode` 文件夹，在该文件夹下面新建 `settings.json` 文件 。主要通过两个配置来实现搜索时排除的目录，和在文件列表中隐藏的文件类型，分别是：`search.exclude` 和 `files.exclude`。在该文件中输入代码 (其中 ** 表示在任意目录下的文件夹)：

```json
{
    "files.associations": {
        "os_task.h": "c"
    },

    "search.exclude": {
        "**/.git"           :true
    },

    "files.exclude": {
        "**/.git"           :true
    }
}
```

参考文档：https://zhuanlan.zhihu.com/p/577742998

## 代码统计工具

- 代码统计工具，支持多平台使用、多语言识别，能够计算指定目标文件或文件夹中的文件数（files）、空白行数（blank）、注释行数（comment）和代码行数（code）：[cloc](https://github.com/AlDanial/cloc)

## 代码格式化工具

- 代码格式化小工具：Astyle，可以将[ Astyle 集成到 Keil 中进行代码格式化](https://jingyan.baidu.com/article/f3e34a12d7d6e5f5eb6535c5.html)，非常方便

## CI/CD

- [TravisCI](https://travis-ci.com/)
- [CircleCI](https://circleci.com/)
- [Jenkins](https://www.jenkins.io/)
- [Drone](https://drone.io/)

## 录屏软件

- 非常简洁好用的录屏软件：[Camtasia 9](https://www.isharepc.com/1884.html)

## 搜索工具

- 速度最快的文件搜索软件：[Everything](http://www.pc6.com/softview/SoftView_53886.html)
- 一款非常专业的搜索工具，[FileLocator Pro](https://www.jb51.net/softs/558967.html) 可以帮助你快速高效的从众多文件夹中找到你的所要的文件数据，FileLocator Pro 可以从指定文件中搜索，也可从全文搜索

## 时间管理工具

- 简洁好用的任务管理工具 [Microsoft To Do](https://to-do.live.com/tasks/myday) 

## 流程图以及脑图

- 流程图绘制软件：[Processon](https://www.processon.com/) 一款简单易用的免费在线作图，实时协作软件
- 脑图绘制软甲: [MindMaster](http://www.edrawsoft.cn/mindmaster/) 拥有非常丰富的模板，制作出的脑图非常漂亮，目前推出了网页版和手机客户端，强烈推荐

## 文件系统读取软件

- 体积小巧功能强大的 img 镜像管理制作工具 : [WinImage](http://www.winimage.com/download.htm)，可以让你轻松读取文件系统镜像中的文件内容

## linux 下简洁的串口工具

- apt install cutecom

## 可能用到的自动化绘图工具

- [Graphviz](https://graphviz.org/)

Graphviz (short for Graph Visualization Software) is a package of open-source tools initiated by AT&T Labs Research for drawing graphs specified in DOT language scripts having the file name extension "gv". It also provides libraries for software applications to use the tools. 

- DOT (graph description language)

## 数学表达式 LaTeX 渲染工具

- Typora 中可以选择数学公式 inline 的渲染方式
- VScode 中可以安装 [Markdown+Math](https://marketplace.visualstudio.com/items?itemName=goessner.mdmath) 来支持 LaTeX 的渲染
- 在 Google 浏览器上可以使用插件 [TeX All the Thing](https://chrome.google.com/webstore/detail/tex-all-the-things/cbimabofgmfdkicghcadidpemeenbffn?hl=en-US) 来支持网页的 LaTeX 渲染和公式的拷贝
- [LaTeX 公式编辑器](https://www.latexlive.com/##)可以处理一些公式的编辑以及图片转换等功能
