# 大纲

- [大纲](#大纲)
  - [块元素](#块元素)
    - [段落与换行符](#段落与换行符)
    - [标题](#标题)
    - [引用文字](#引用文字)
    - [列表](#列表)
    - [任务列表](#任务列表)
    - [(栅栏式)代码块](#栅栏式代码块)
    - [数学公式（待完善）](#数学公式待完善)
    - [表格](#表格)
    - [脚注](#脚注)
    - [水平线](#水平线)
    - [目录](#目录)
    - [YAML Front Matter（待完善）](#yaml-front-matter待完善)
    - [图表 (Sequence, Flowchart and Mermaid)](#图表-sequence-flowchart-and-mermaid)
      - [序列图（Sequence）](#序列图sequence)
        - [标题](#标题-1)
        - [对象](#对象)
        - [消息（Note）](#消息note)
        - [交互（actor）](#交互actor)
        - [示例](#示例)
      - [流程图（Flowchart）](#流程图flowchart)
        - [节点类型](#节点类型)
        - [连接](#连接)
          - [方向](#方向)
        - [示例](#示例-1)
      - [美人鱼（Mermaid）官网 （待完善）](#美人鱼mermaid官网-待完善)
  - [Span 元素](#span-元素)
    - [链接](#链接)
      - [内部链接](#内部链接)
      - [参考链接](#参考链接)
      - [URL 网址](#url-网址)
      - [图片](#图片)
    - [强调（斜体）](#强调斜体)
    - [强调（粗体）](#强调粗体)
    - [代码](#代码)
    - [删除线](#删除线)
    - [下划线](#下划线)
    - [表情符号](#表情符号)
    - [内联数学公式（待完善）](#内联数学公式待完善)
    - [上标](#上标)
    - [下标](#下标)
    - [高亮](#高亮)
  - [HTML](#html)
    - [嵌入内容](#嵌入内容)
    - [视频](#视频)
    - [其他 HTML 支持](#其他-html-支持)
      - [内联 HTML](#内联-html)
      - [HTML 实体](#html-实体)
        - [不间断空格](#不间断空格)
        - [HTML 字符实体](#html-字符实体)
        - [结合音标符](#结合音标符)
        - [其它全部字符集](#其它全部字符集)
          - [HTML ASCII 字符](#html-ascii-字符)
          - [HTML Windows-1252 (ANSI)字符集](#html-windows-1252-ansi字符集)
          - [HTML ISO-8859 字符集](#html-iso-8859-字符集)

## 块元素

### 段落与换行符

​ 在 markdown 源代码中，段落由多个空行分隔。大多数 markdown 解析器会忽略单行中断，要使其他 markdown 解析器识别的换行符，可以在行尾留下两个空格，或者插入 `<br/>`。

### 标题

​ 标题在行的开头使用 1-6 个＃字符，对应于标题级别 1-6。例如：

```Markdown
# 这是一级标题
## 这是二级标题
###### 这是六级标题
```

### 引用文字

​ Markdown 使用 `>`字符进行块引用。例如：

```Markdown
> 这是一个有两段的块引用。这是第一段。
>
> 这是第二段。Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.



> 这是另一个只有一个段落的块引用。有三个空行分隔两个块引用
```

​ 通过添加额外级别的“>”允许在块引用内嵌入另一个块引用。

### 列表

​ 输入 `+ list item 1` 将创建一个无序列表，该 `+` 符号可以替换为 `-` 或 `*`。

​ 输入 `1. list item 1` 将创建一个有序列表，其代码如下：

```Markdown
## 无序列表
+ 红色
+ 绿色
+ 蓝色

## 有序列表
1. 红色
2. 绿色
3. 蓝色
```

### 任务列表

​ 任务列表是标记为`[ ]`或`[x]`（未完成或完成）的项目的列表 ,书写方式为`-` `空格` `[` `空格` `]`。例如：

```Markdown
- [ ] 这是一个任务列表项
- [ ] 需要在前面使用列表的语法
- [ ] normal **formatting**, @mentions, #1234 refs
- [ ] 未完成
- [x] 完成
```

### (栅栏式)代码块

​ 输入` ``` ` 之后输入一个可选的语言标识符，然后按`return`键后输入代码:

```js
function test() {
  console.log("notice the blank line before this function?");
}
```

````gfm
``` ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```
````

### 数学公式（待完善）

​ 使用 **MathJax** 渲染 _LaTeX_ 数学表达式。

​ 输入 `$$`, 然后按`Enter`键将触发一个接受_Tex / LaTex_源代码的输入区域。

```latex
$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix}
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
\end{vmatrix}
$$
```

$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix}
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
\end{vmatrix}
$$

### 表格

​ 输入`| First Header | Second Header |`后将创建一个包含两列的表。

```Markdown
| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |
```

​ 在表格中包括内联 Markdown 语法，例如链接，粗体，斜体或删除线。

​ 并且通过在标题行中包含冒号`:`您可以将文本定义为左对齐，右对齐或居中对齐：

```Markdown
| Left-Aligned  | Center Aligned  | Right Aligned |
| :------------ |:---------------:| -----:|
| col 3 is      | some wordy text | $1600 |
| col 2 is      | centered        |   $12 |
| zebra stripes | are neat        |    $1 |
```

​ 最左侧的冒号表示左对齐的列; 最右侧的冒号表示右对齐的列; 两侧的冒号表示中心对齐的列。

### 脚注

```Markdown
创建脚注[^footnote].

[^footnote]: 这是**脚注**的*文本*
```

您可以像这样创建脚注[^1]

[^1]: 这是脚注

### 水平线

​ 输入 `***` 或 `---` 在空行上将会形成一条水平线。

---

### 目录

​ 输入`[TOC]`将自动创建一个自动更新的目录。

### YAML Front Matter（待完善）

​ Typora 现在支持 [YAML Front Matter](http://jekyllrb.com/docs/frontmatter/) 。 在文章顶部输入 `---` 然后按 `Enter` 键将引入一个，或者从菜单中插入一个元数据块。

### 图表 (Sequence, Flowchart and Mermaid)

#### 序列图（Sequence）

##### 标题

```
title:序列图标题
```

如图：

```sequence
title:序列图标题
```

##### 对象

```
participant 对象1
participant 对象2
```

如图：

```sequence
participant 对象1
participant 对象2
```

##### 消息（Note）

```
participant 对象1
Note left of 对象1:这是左面的消息
participant 对象2
Note over 对象2:这是中间的消息
participant 对象3
Note right of 对象3: 这是右面的消息
```

如图：

```sequence
participant 对象1
Note left of 对象1:这是左面的消息
participant 对象2
Note over 对象2:这是中间的消息
participant 对象3
Note right of 对象3: 这是右面的消息
```

##### 交互（actor）

```
participant 对象1
participant 对象2
participant 对象3
participant 对象4
对象1->对象2
```

```sequence
对象1->对象2:实线实箭头
对象1->>对象3:实线虚箭头
对象1-->对象4:虚线实箭头
对象1-->>对象5:虚线虚箭头
```

##### 示例

```sequence
title:标题
A->B: 实线实箭头
B->>C: 实线虚箭头
C-->D: 虚线实箭头
D-->>A: 虚线虚箭头

Note left of A: A的\n左侧消息
Note right of A: A的\n右侧消息
Note over A: A的\n中间消息
Note over C,D: 覆盖C，D的消息
```

#### 流程图（Flowchart）

​ 流程图的语法大体分为两部分：

- 前面部分用来定义流程图元素；
- 后面部分用来连接流程图元素，指定流程图的执行走向。

​ **定义元素阶段的语法是**

```clojure
tag=>Type: content[|flowstate][:>url]
```

- tag 是流程图中的标签，在第二段连接元素时会用到。名称可以任意，一般为流程的英文缩写和数字的组合。
- type 用来确定标签的类型，`=>`后面表示类型。由于标签的名称可以任意指定，所以必须依赖 type 来确定标签的类型。
- 标签有 6 种类型：`start` `end` `operation` `subroutine` `condition` `inputoutput`。
- content 是流程图文本框中的描述内容，中英文均可。特别注意，冒号与文本之间一定要有个`空格`，允许使用换行符，并将反映在文本中。
- flowstate 是可选的，它是为节点指定额外样式的运算符。
- url 是可选的连接，与相绑定，`:>`后面就是对应的 url 链接，点击文本时可以通过链接跳转到 url 指定页面。

##### 节点类型

​ **定义节点形状**

1. 开始

   用作流程图开始的节点，缺省文本为 `start`。

   ```flowchart
   st=>start: 开始
   ```

2. 结束

   用作流程图结束的最后一个节点，缺省文本为 `End`。

   ```flowchart
   e=>end: 结束
   ```

3. 操作

   指示在流程图中执行操作的节点，缺省文本为 `operation`。

   ```flowchart
   op1=>operation: 操作
   ```

4. 输入/输出

   表明流程图中发生的 I/O

   ```flowchart
   io=>inputoutput: I/O
   ```

5. 子程序

   表明流程图中发生了一个子例程，且应有另一个流程图来记录此子程序。

   ```flowchart
   sub=>subroutine: 子程序
   ```

6. 条件

   条件语句或逻辑语句将流程图指向到两个路径之一。

   ```flowchart
   cond=>condition: 判断条件
   Yes or No?
   ```

7. 平行

   允许多个流程图同时发生。

   ```flowchart
   para=>parallel: 平行
   ```

##### 连接

​ 连接在节点定义下方的定义部分中定义。运算符指定从一个节点到另一个节点的连接，如 ：`->` `节点1->节点2->节点3`。

​ 并非所有节点都需要在一个字符串中连接，并且可以分离，例如：

```flowchart
节点1->节点2
节点2->节点3
```

​ 连接语法如下：（ `[]` 中项目是可选的）

```flowchart
<变量名1>[(<说明1>[,<说明2>])]-><变量名2>[(<说明1>[,<说明2>])]-><变量名3>
```

###### 方向

​ 每个元素可以制定分支走向，默认向下，也可以用`right`指向右边

- top（上）
- bottom（下）
- left（左）
- right（右）

```flowchart
parallelVar(path1, <direction>)->nextNode1
parallelVar(path2, <direction>)->nextNode2
parallelVar(path3, <direction>)->nextNode3
```

##### 示例

```flowchart
st=>start: Start:>https://www.baidu.com[blank]
e=>end:>https://www.baidu.com
op1=>operation: 操作
sub1=>subroutine: 子程序
cond=>condition: 线性还是多项式 :>https://www.baidu.com
io=>inputoutput: 捕捉中……
para=>parallel: 三种可能

st->op1->cond
cond(true@线性)->io->e
cond(false@多项式)->sub1(right)
sub1(right)->para
para(path1@an1, top)->cond
para(path2@an2, right)->op1
para(path3@an3, bottom)->e
```

```flow
st=>start: Start:>https://www.baidu.com[blank]
e=>end:>https://www.baidu.com
op1=>operation: 操作
sub1=>subroutine: 子程序
cond=>condition: 线性还是多项式 :>https://www.baidu.com
io=>inputoutput: 捕捉中……
para=>parallel: 三种可能

st->op1->cond
cond(true@线性)->io->e
cond(false@多项式)->sub1(right)
sub1(right)->para
para(path1@an1, top)->cond
para(path2@an2, right)->op1
para(path3@an3, bottom)->e
```

#### 美人鱼（Mermaid）[官网](https://mermaid-js.github.io/mermaid/#/) （待完善）

​ **Mermaid 允许您使用文本和代码创建图表和可视化效果。**

## Span 元素

​ 输入 Span 元素会被立即解析并呈现。在这些 span 元素上移动光标会将这些元素扩展为 markdown 源代码。

### 链接

​ Markdown 支持两种类型的链接：内联和引用。链接文本都写在[方括号]内。

​ 创建内联链接，在链接文本的结束方括号后立即使用一组常规括号。在常规括号内，输入 URL 地址，以及可选的用引号括起来的链接标题。例如：

```Markdown
这是一个内联链接的[例子](https://www.baidu.com/ "标题")

[这个链接](https://www.baidu.com/) 没有标题属性。
```

​ 这是一个内联链接的[例子](https://www.baidu.com/ "标题") 。(`<p>这是一个内联链接的<a href="https://www.baidu.com/" title="Title">例子</a>`)

[这个链接](https://www.baidu.com/) 没有标题属性。 (`<p><a href="https://www.baidu.com/">这个链接</a>没有标题属性`)

#### 内部链接

​ **将常规括号内的 href 设置为文档内的某一个标题**，将创建一个书签，在单击后跳转到该部分。例如：

`Ctrl` + `左键单击` [这个连接](# 块元素)将跳转到标题 `块元素`处。

#### 参考链接

​ 参考样式链接使用两组方括号，在其中输入选择的标签以标识链接：

```Markdown
这是一个链接[示例][id]
然后，在文档中的任何位置，可以单独定义链接标签，如下所示：
[id]: https://www.baidu.com/ "百度"
```

​ 这是一个链接[示例][id]

[id]: https://www.baidu.com/ "百度"

隐式链接名称快捷方式允许省略链接的名称，在这种情况下，链接文本本身将用作名称。只需使用一组空的方括号，例如，将“Google”一词链接到 google.com 网站:

```Markdown
[Baidu][]
然后定义链接：
[Baidu]: https://www.baidu.com/
```

[Baidu][]
然后定义链接：

[baidu]: https://www.baidu.com/

#### URL 网址

`<i@typora.io>` 成为 [i@typora.io](mailto:i@typora.io)。

亦或直接输入标准 URL 链接www.baidu.com

#### 图片

​ 图像与链接类似， 但在链接语法之前需要添加额外的 `!` 字符。如下：

```Markdown
![替代文字](/path/to/img.jpg)

![替代文字](/path/to/img.jpg "可选标题")
```

### 强调（斜体）

​ Markdown 将星号 `*`和下划线`_` 视为强调的指示。用一个 `*` or `_` 包裹文本将使用 HTML `<em>` 标签包裹文本。例如：

```Markdown
*单个星号*

_单个下划线_
```

​ 将输出：

_单个星号_

_单个下划线_

​ GFM 将忽略单词中的下划线，通常用在代码和名称中，如下所示：

> wow_great_stuff
>
> do_this_and_do_that_and_another_thing.

要在用作强调分隔符的位置生成文字星号或下划线，可以用反斜杠转义：

```Markdown
\*这个文字被文字星号包围\*
```

### 强调（粗体）

​ 用两个 `*` 或 `_` 包裹的文本将使用 HTML `<strong>` 标签包裹，例如：

```Markdown
**双星号**

__双重下划线__
```

​ 输出：

​ **双星号**

​ **双重下划线**

### 代码

​ 要指示代码范围，使用反引号`` `进行包裹。与预格式化的代码块不同，代码跨度表示正常段落中的代码。例如：

```Markdown
使用`printf()`函数。
```

输出：

使用`printf()`函数。

### 删除线

GFM 通过添加语法来创建删除线文本，标准的 Markdown 中缺少该文本。

​ `~~错误的文字。~~` 变成 ~~错误的文字。~~

### 下划线

​ 下划线由原始 HTML 提供支持。

​ `<u>下划线</u>` 变成<u>下划线</u>

### 表情符号

​ 输入表情符号的语法是 `:smile:` :smile:

### 内联数学公式（待完善）

​ 使用 `$` 来包裹 TeX 命令，例如： `$\lim_{x \to \infty} \exp(-x) = 0$` 将呈现为 LaTeX 命令。

​ $\lim_{x \to \infty} \exp(-x) = 0$

### 上标

​ `^` 来包裹上标内容，例如： `X^2^` (X^2^)。

### 下标

​ 用 `~` 来包裹下标内容，例如： `H~2~O` (H~2~0), `X~long\ text~` (X~long\ text~)。

### 高亮

​ 用 `==` 来包裹高亮内容，例如： `==highlight==` (==highlight==)。

## HTML

​ 可以使用 HTML 来设置纯 Markdown 不支持的内容，例如，`<span style="color:red">this text is red</span>`用于添加红色文本。

### 嵌入内容

​ 有些网站提供基于 iframe 的嵌入代码，例如：

```Markdown
<iframe height='265' scrolling='no' title='Fancy Animated SVG Menu' src='http://codepen.io/jeangontijo/embed/OxVywj/?height=265&theme-id=0&default-tab=css,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'></iframe>
```

### 视频

​ 您可以使用 `<video>` 标记嵌入视频，例如：

```Markdown
<video src="xxx.mp4" />
```

### 其他 HTML 支持

#### 内联 HTML

| 原始 Markdown 输入                                               | 实时预览中的输出                                               |
| ---------------------------------------------------------------- | -------------------------------------------------------------- |
| `<span style='color:red'>这是红色的</span>`                      | <span style='color:red'>这是红色的</span>                      |
| `<ruby> 漢 <rt> ㄏㄢˋ </rt> </ruby>`                             | <ruby> 漢 <rt> ㄏㄢ ˋ </rt> </ruby>                            |
| `<kbd>Ctrl</kbd>+<kbd>F9</kbd>`                                  | <kbd>Ctrl</kbd>+<kbd>F9</kbd>                                  |
| `<span style="font-size:2rem; background:yellow;">**大**</span>` | <span style="font-size:2rem; background:yellow;">**大**</span> |
| `HTML实体，如：&reg; &#182;`                                     | HTML 实体，如： &reg; &#182;                                   |

#### HTML 实体

​ HTML 中的保留字符必须替换为字符实体。若在文本中使用小于 (`<`) 或大于 (`>`) 符号，浏览器可能会将它们与标签混合。

​ 如果希望正确地显示预留字符，必须在 HTML 源代码中使用字符实体，如下：

> &实体名称;
> 或
> &#实体编号;

> **使用实体名称的好处：**实体名称容易记忆。
> **使用实体名称的缺点：**浏览器可能不支持所有实体名称，但对实体编号的支持很好。

##### 不间断空格

​ HTML 中的常用字符实体是不间断空格(`&nbsp;`)。

​ 不间断空格是不会换行的空格。由不间断空格分隔的两个单词将粘在一起（不换行）。当破坏单词可能具有破坏性时，这很方便。例如：

- §&nbsp;10
- 10&nbsp;公里/小时

​ 浏览器总是会截短 HTML 页面中的空格。如果在文本中写 10 个空格，在显示该页面之前，浏览器会删除它们中的 9 个。如需在页面中增加空格的数量，需要使用 `&nbsp;` 字符实体。

不间断连字符（ `&#8209;` ,&#8209;）用于定义不换行的连字符 (‑)。

##### HTML 字符实体

| 显示结果 | 描述        | 实体名称   | 实体编号  |
| :------- | :---------- | :--------- | :-------- |
|          | 空格        | `&nbsp;`   | `&#160;`  |
| <        | 小于号      | `&lt;`     | `&#60;`   |
| >        | 大于号      | `&gt;`     | `&#62;`   |
| &        | 和号        | `&amp;`    | `&#38;`   |
| "        | 双引号      | `&quot;`   | `&#34;`   |
| '        | 单引号      | `&apos;`   | `&#39;`   |
| ¢        | 分          | `&cent;`   | `&#162;`  |
| £        | 镑          | `&pound;`  | `&#163;`  |
| ¥        | 人民币/日元 | `&yen;`    | `&#165;`  |
| €        | 欧元        | `&euro;`   | `&#8364;` |
| §        | 小节        | `&sect;`   | `&#167;`  |
| ©        | 版权        | `&copy;`   | `&#169;`  |
| ®        | 注册商标    | `&reg;`    | `&#174;`  |
| ×        | 乘号        | `&times;`  | `&#215;`  |
| ÷        | 除号        | `&divide;` | `&#247;`  |

##### 结合音标符

​ 1. 发音符号是加到字母上的一个"glyph(字形)"，如尖音符（`̀`）和 抑音符（`́`）。

​ 2. 变音符号可以出现字母的上面和下面，或者字母里面，或者两个字母间。

3. 变音符号可以与字母、数字字符的组合来使用。

​ 例如：

| 音标符 | 字符 | 代码      | 输出    |
| ------ | ---- | --------- | ------- |
| ̀       | a    | `a&#768;` | a&#768; |
| ́       | a    | `a&#769;` | a&#769; |
| ̂       | a    | `a&#770;` | a&#770; |
| ̃       | a    | `a&#771;` | a&#771; |

##### 其它全部字符集

###### HTML ASCII 字符

详见[W3C ASCII 字符集](https://www.w3schools.com/charsets/ref_html_ascii.asp)

###### HTML Windows-1252 (ANSI)字符集

详见[W3C WIN-1252 字符集](https://www.w3schools.com/charsets/ref_html_ansi.asp)

###### HTML ISO-8859 字符集

详见[W3C ISO-8859 字符集](https://www.w3schools.com/charsets/ref_html_8859.asp)
