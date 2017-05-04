## Typora使用

windows版下载地址：https://www.typora.io/#windows
众多的 Markdown 编辑器里，能看的过眼都是 macOS 下，Windows 真是…可怜。
可能是 Windows 的开发者被微软带坏了，作为一款合格的 Markdown 编辑器，Typora 支持图片、列表、表格、代码、公式、目录等功能，并且有多种主题模板，默认主题依旧来自 Github。

### 介绍

http://www.jianshu.com/p/5256ecc06eec

http://blog.csdn.net/qq_21184771/article/details/57466568

https://sspai.com/post/30292

### 语法

https://sanwen8.cn/p/7e2nNIb.html

- markdown使用

  1. 标题

     如果一段文字被定义为标题，只要在这段文字前加 `#` 号即可。

     `# 一级标题`

     `## 二级标题`

     `### 三级标题`

     以此类推，总共六级标题，建议在井号后加一个空格，这是最标准的 Markdown 语法。

  2. 列表(有序和无序)

     在 Markdown 下，列表的显示只需要在文字前加上 `-` 或 `*` 即可变为无序列表，有序列表则直接在文字前加 `1.` `2.` `3.` 符号要和文字之间加上一个字符的空格。

  3. 引用

     > here

     如果你需要引用一小段别处的句子，那么就要用引用的格式。

     `> 例如这样`

     只需要在文本前加入 `>` 这种尖括号（大于号）即可

  4. 图片与链接

     如：[百度](www.baidu.com)

     ![图](https://cdn.sspai.com/attachment/origin/2014/04/15/69495.jpg?imageMogr2/quality/90/thumbnail/700x)

     插入链接与插入图片的语法很像，区别在一个 `!`号

     插入图片的地址需要图床，这里推荐 [CloudApp](http://www.getcloudapp.com/) 的服务，生成URL地址即可。

  5. 粗体与斜体

     Markdown 的粗体和斜体也非常简单，用两个 `*` 包含一段文本就是粗体的语法，用一个 `*` 包含一段文本就是斜体的语法。

     **粗体**

     *斜体*

     例如：**这里是粗体** *这里是斜体*

  6. 表格

     表格是我觉得 Markdown 比较累人的地方，例子如下：

     |  a   |  b   |  c   |
     | :--: | :--: | :--: |
     |  1   |  2   | test |
     |  r   |  2   |  r   |

  7. 代码块

     如果你是个程序猿，需要在文章里优雅的引用代码框，在 Markdown 下实现也非常简单，只需要用两个 ` 把中间的代码包裹起来，如 `code`。图例：

     三个`，写语言

     `code`

     ```java
      @RequestMapping("/show")
         public String showSomeThing(){
             return demoService.showStr("showSomeThing");
         }
     ```

  8. 分割线

     分割线的语法只需要另起一行，连续输入三个星号 `***` 即可。

     ***

- 相关链接

  https://sspai.com/post/25137

  ***

  ​


http://www.appinn.com/markdown/

http://www.williamlong.info/archives/4319.html