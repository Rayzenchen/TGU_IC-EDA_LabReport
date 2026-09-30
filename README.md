# 天津工业大学 · 集成电路EDA 实验报告 LaTeX 模板

模板作者：陈睿晢（物理2403）。MIT 许可，转发、修改请保留署名。

最新版：<https://github.com/Rayzenchen/tjpu-ic-eda-lab-report>（右上角 Code → Download ZIP）

封面按学校《实验报告封面格式》排版，正文固定四节：实验目的、实验步骤、扩展内容、实验总结。一个项目可以写完整个学期的所有实验报告。

## 开始使用

### Overleaf（推荐）

1. Overleaf 首页 → New Project → Upload Project，上传本模板的 ZIP。
2. **把编译器改成 XeLaTeX**：左上角 Menu → Settings → Compiler 选 `XeLaTeX`。Overleaf 默认是 pdfLaTeX，不改会直接报错 `Compiler must be XeLaTeX`。这一步模板没法替你做，每个新项目都要改一次。
3. 点 Recompile，能看到示例报告就说明环境没问题。

### 本地编译

装好 TeX Live 或 MiKTeX，在项目根目录运行：

```bash
latexmk -xelatex main.tex
```

## 写一篇新报告

1. 把 `shared/skeleton/` 整个复制一份，改名为 `实验N_题目`，比如 `实验2_反相器原理图`。文件夹名不要带空格。
2. 打开新文件夹里的 `main.tex`，把所有 `shared/skeleton` 替换成新文件夹名（一处 `\docdir`、四处 `\input`）。
3. 在同一个文件里填写报告信息：`\labtitle`（题目）、`\classname`（班级）、`\studentid`（学号）、`\studentname`（姓名）、`\reportdate`（日期）。
4. 把项目根目录 `main.tex` 的最后一行改成 `\input{实验N_题目/main.tex}`。
5. 在 `sections/` 下的四个文件里写正文。

Overleaf 始终从项目根目录编译，所以所有 `\input` 和路径都要从根目录开始写，不能写 `../`。

## 常用写法

`实验0_模板示例/` 里每种写法都演示了一次，可以对照着看。

| 需求 | 写法 |
|---|---|
| 插入截图 | 图片放进 `<报告文件夹>/figs/`，写 `\labfig{文件名.png}{图题}{fig:标签}`；图片还没放时显示灰色占位框 |
| 指定图宽 | `\labfig[0.5\textwidth]{文件名.png}{图题}{fig:标签}` |
| 终端命令 | `\begin{lstlisting}[style=shell] … \end{lstlisting}` |
| 引用图表 | `如图~\ref{fig:标签}`、`见表~\ref{tab:标签}` |
| 步骤分节 | `\subsection{…}`，显示为「第一部分：…」 |

## 文件结构

```text
main.tex               # 编译开关：只有最后一行 \input 需要改
shared/
  preamble.tex         # 版式、宏包、\labfig 等命令、报告信息默认值
  cover.tex            # 封面
  skeleton/            # 新报告的空白骨架
实验0_模板示例/         # 示例报告（可以删掉）
AGENTS.md              # 给 AI 看的使用规则
```

调版式只改 `shared/`，所有报告会一起生效。

## 让 AI 帮忙写

把整个项目（或 ZIP）连同实验指导书、截图一起交给 AI，并告诉它先读 `AGENTS.md`。里面写好了怎么建文件夹、四节分别写什么、截图怎么放。AI 写完后，请自己核对内容，并用自己的话修改。报告是交给老师的作业，照抄别人的报告不可取。

## 常见问题

- **报错 `Compiler must be XeLaTeX`**：编译器没改，见上面第 2 步。
- **姓名里的生僻字显示成方框**：模板会在缺字时自动改用 Noto Serif CJK SC。Overleaf 上已自带这个字体；本地编译时如果还缺字，请安装 Noto Serif CJK SC。
- **图片没显示、只有灰框**：检查文件是否放在 `<报告文件夹>/figs/` 下，以及文件名（包括扩展名大小写）是否和 `\labfig` 里写的一致。
