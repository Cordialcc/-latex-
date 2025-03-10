## ElegantNote 模板使用说明

模板来自 `elegantnote`。

### 1. 编译方式

*   **推荐：** XeLaTeX 中
*   **支持:** pdfLaTeX 英(功能受限, 例如无法使用 `founder` 中文字体选项)

### 2. 文档类和选项

使用 `\documentclass[选项]{elegantnote}` 命令来设置文档的整体样式.

**主要选项 (用逗号分隔):**

| 选项类别      | 选项                                | 描述                                                                                   | 默认值   |
| :------------ | :---------------------------------- | :------------------------------------------------------------------------------------- | :------- |
| **语言 (lang)**   | `cn`                                | 中文模式 (Chinese)                                                       | `cn`     |
|               | `en`                                | 英文模式 (English)                                                      |          |
| **纸张模式 (mode)** | `hazy`                              | 朦胧模式（淡蓝色背景）                                                                 | `hazy` |
|               | `geye`                              | 护眼模式（绿豆沙背景）                                                                  |        |
| **设备 (device)**| `pad`                               | 适配 iPad 屏幕                                                                       | `pad`    |
|               | `kindle`                            | 适配 Kindle 屏幕                                                                    |          |
|               | `pc`                                | 双页模式，适合电脑阅读                                                                   |          |
|               | `normal`                            | 普通 A4 纸张大小                                                                     |          |
|    |`screen`| 4:3 PPT 大小| |
| **颜色主题 (color)** | `blue`                              | 蓝色                                                                                   | `blue`   |
|               | `green`                             | 绿色                                                                                   |          |
|               | `cyan`                              | 青色                                                                                   |          |
|               | `sakura`                            | 樱花粉                                                                               |          |
|               | `black`                             | 黑色（无颜色）                                                                         |          |
| **数学字体 (math)** | `cm`                                | 默认 LaTeX 数学字体 (Computer Modern)                                                  | `cm`     |
|               | `newtx`                             | 使用 `newtxmath` 包设置数学字体                                                            |          |
|               | `mtpro2`                            | 使用 `mtpro2` 包设置数学字体 (需安装)                                                       |          |
| **中文字体 (chinesefont)** | `ctexfont`                       | 使用 `ctex` 宏包自动选择系统字体 (可能缺失)                                                        | `ctexfont`     |
|        |`founder`| 使用方正字体 (需安装, 且必须使用 XeLaTeX) | |
|    | `nofont`                            | 不设置中文字体，用户自定义 (需使用 XeLaTeX)                                                    |          |
| **全局字体大小** | `8pt`, `9pt`, `10pt`, `11pt`, `12pt`, `14pt`, `17pt`, `20pt` | 设置文档全局字体大小                                                       | `10pt` |
|**参考文献格式(cite)**|`authoryear`,`numbers`,`super`| 设置参考文献格式| `numbers`|

**示例：**

```latex
\documentclass[cn, hazy, pad, green, math=cm, 12pt]{elegantnote}
```

### 3. 文档元数据

| 命令               | 描述           | 示例                                   |
| :----------------- | :------------- | :------------------------------------- |
| `\title{}`         | 文档标题       | `\title{C++ Programming}`              |
| `\author{}`        | 作者           | `\author{代继栋}`                       |
| `\version{}`      | 版本号         | `\version{0.1.0.0}`                    |
| `\date{}`         | 日期           | `\date{\zhdate{2025/3/10}}` (中文日期) |
|                    |                | `\date{}` (不显示日期)                    |
| `\institute{}`|作者单位| `\institute{Elegant\LaTeX{} Program}` |

**注意**:
*   要使用中文日期格式, 需要 `\zhdate{}` 命令 (来自 `zhnumber` 包).
*  `\date{}` 不写日期参数, 则会使用当日日期.
*  `\version{}` 不写则不会显示版本信息.

### 4.  文档结构

| 命令/环境                     | 描述                               |
| :---------------------------- | :--------------------------------- |
| `\maketitle`                   | 创建标题页                           |
| `\section{}`                  | 一级标题                           |
| `\subsection{}`               | 二级标题                           |
| `\subsubsection{}`            | 三级标题                           |
| `\paragraph{}`                 | 段落标题 (不编号)                  |
| `\subparagraph{}`              | 子段落标题 (不编号)                |
| `{itemize}`                   | 无序列表                           |
| `{enumerate}`                 | 有序列表                           |
| `{description}`               | 描述列表                           |
|`\printbibliography`|打印参考文献列表|

### 5.  常用环境

| 环境         | 描述         | 示例                                                                                  |
| :----------- | :----------- | :------------------------------------------------------------------------------------ |
| `remark`     | 备注         | `\begin{remark} ... \end{remark}`                                                        |
| `note`       | 注释         | `\begin{note} ... \end{note}`                                                            |
| `theorem`    | 定理         | `\begin{theorem}[可选标题] ... \end{theorem}`                                                  |
| `lemma`      | 引理         | `\begin{lemma} ... \end{lemma}`                                                            |
| `definition` | 定义         | `\begin{definition} ... \end{definition}`                                                |
| `proof`      | 证明         | `\begin{proof} ... \end{proof}`                                                          |
| `equation`   | 带编号的公式 | `\begin{equation} \label{eq:label} ... \end{equation}` (使用 `\ref{eq:label}` 引用) |
| `figure`     | 浮动图       | `\begin{figure}[!htb] \centering \includegraphics[width=0.9\textwidth]{...} \caption{} \label{} \end{figure}` |
| `table`      | 浮动表格      | `\begin{table}...\end{table}`                                                 |
| `lstlisting` | 代码         |\begin{lstlisting} ... \end{lstlisting}   或者 `\lstinline{...}`|

### 6.  常用命令

| 命令                    | 描述               | 示例                               |
| :---------------------- | :----------------- | :--------------------------------- |
| `\usepackage{}`         | 导入宏包           | `\usepackage{amsmath}`              |
| `\textcolor{颜色}{文本}` | 设置文本颜色       | `\textcolor{red}{Hello}`           |
| `\textbf{}`             | 粗体               | `\textbf{Bold}`                    |
| `\textit{}`             | 斜体               | `\textit{Italic}`                  |
| `\kaishu`              |楷书(自定义命令)|  `\kaishu 中文`|
| `\fangsong`            |仿宋(自定义命令)|   `\fangsong 中文`|
| `\heiti`                 | 黑体(自定义命令)          | `\heiti 中文` |
| `\songti`                 | 宋体 (自定义命令)   | `\songti 中文`            |
| `\label{}`             | 设置标签           | `\label{sec:intro}`                |
| `\ref{}`               | 引用标签           | `\ref{sec:intro}`                  |
| `\eqref{}`              | 引用公式标签       | `\eqref{eq:label}`                 |
| `\footnote{}`          | 脚注               | `\footnote{This is a footnote.}`  |
| `\includegraphics{}`    | 插入图片           | `\includegraphics[width=0.5\textwidth]{image.jpg}` |
|`\lstinline{}`| 行内代码 | `\lstinline{printf("Hello");}`|
|`\zhdate{}`| 中文日期格式化| `\zhdate{2024/5/13}`|

### 7.  数学公式

*   **行内公式：**  使用 `$...$` 包围，例如 `$x^2 + y^2 = z^2$`。
*   **行间公式 (不编号)：** 使用 `\[ ... \]` 包围。
*   **行间公式 (编号)：** 使用 `\begin{equation} ... \end{equation}` 环境, 并用`\label` 和 `\ref` 来进行引用。
*  **上下标:** `a_i`, `b^2`, `{}` 用于分组, 如`x_{i,j}`
* **常见符号:** 分数`\frac{1}{2}`, 求和`\sum_{i=1}^n`, 积分 `\int_a^b`, 极限 `\lim_{x \to \infty}`, 希腊字母 `\alpha`, `\beta`, `\gamma`, `\Delta`

### 8.  自定义中文字体 (chinesefont=nofont)

如果选择 `chinesefont=nofont`，你需要在导言区手动设置中文字体。 示例 (以方正字体为例)：

```latex
\setCJKmainfont[BoldFont={FZHei-B01},ItalicFont={FZKai-Z03}]{FZShuSong-Z01}
\setCJKsansfont[BoldFont={FZHei-B01}]{FZKai-Z03}
\setCJKmonofont[BoldFont={FZHei-B01}]{FZFangSong-Z02}
\setCJKfamilyfont{zhsong}{FZShuSong-Z01}
\setCJKfamilyfont{zhhei}{FZHei-B01}
\setCJKfamilyfont{zhkai}[BoldFont={FZHei-B01}]{FZKai-Z03}
\setCJKfamilyfont{zhfs}[BoldFont={FZHei-B01}]{FZFangSong-Z02}
\newcommand*{\songti}{\CJKfamily{zhsong}}
\newcommand*{\heiti}{\CJKfamily{zhhei}}
\newcommand*{\kaishu}{\CJKfamily{zhkai}}
\newcommand*{\fangsong}{\CJKfamily{zhfs}}
```