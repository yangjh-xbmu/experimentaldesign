# Bookdown 的基本用法 {#basic}

从本质上讲，bookdown 是基于 Pandoc、markdown、R、Rmarkdown、gitbook、tex、git 等等一系列开源项目上的综合性工具，这套工具大大降低了用户自己整合上述多个工具的成本，以更加高效地方式完成内容创作、发布和维护。

## 使用bookdown创作的流程

### 初始化

使用下载的模板或者bookdown自带的模板，创建bookdown项目。建议使用前者，因为更加适合中文内容的排版。

当然，当用户熟悉了bookdown之后，还可以在这些模板的基础上进行必要的配置，使之更加符合用户的需求。

### 编辑内容

在合适的编辑器中（建议先使用RStudio，后期熟悉后，可使用VS Code之类的功能更为复杂的通用性编辑器），按照markdown以及Rmarkdown的语法规则，进行内容的创作和编辑。

### 预览内容

选择 RStudio 中的“`Build Book`”功能，生成合适格式。还可以在控制台中键入如下命令，开启实时预览：

```R
bookdown::serve_book()
```

### 发布

利用 GitHub 或 Gitee 的 page 服务，可将生成的静态页面发布到网络。

## bookdown 对文档的组织

和一篇文章相比，一本书包含多个章节。在bookdown中，一个章节对应一个后缀名为`.Rmd`的 R Markdown 文件，每个 R Markdown 文件（除了首页）都必须以一级标题开头。例如：

```markdown
# bookdown 对书本文档的组织
```

默认情况下，bookdown 按照文件名的顺序，从前到后合并在一起，并渲染成gitbook格式或者pdf、epub或者word文件。

如果存在`index.Rmd`文件，则该文件会被渲染成`index.html`。以下划线开头的文件，会被bookdown忽略。

bookdown 还提供了自定义章节顺序的机制。在配置文件`_bookdown.yml`中，通过`rmd_files`字段实现，例如：

```YAML
rmd_files: ["index.Rmd", "abstract.Rmd", "intro.Rmd"]
```

还可以分别为不同格式指定包含的内容：

```
rmd_files:
  html: ["index.Rmd", "abstract.Rmd", "intro.Rmd"]
  latex: ["abstract.Rmd", "intro.Rmd"]
```

必须要指出的是，每个章节的一级标题后，需要在后面加上标签，如：

```markdown
# Bookdown 的基本用法 {#basic}
```

## bookdown 语法

首先，bookdown是基于markdown和pandoc的工具，因此，[Markdown 的原生语法](https://daringfireball.net/projects/markdown/syntax)肯定是可以使用的。在此不再赘述。

其次，[Pandoc 在markdown语法的基础上，提供了一些增强](https://pandoc.org/MANUAL.html#pandocs-markdown)，bookdown也是支持的。

最后，bookdown 是在 [R bookdown 包](https://rmarkdown.rstudio.com/index.html)的基础上进行扩展，故而也支持 R Markdown 语法。如：


```r
dim(iris)
```

```
## [1] 150   5
```

再如，下面的代码将列出R Markdown支持的所有语言：


```r
names(knitr::knit_engines$get())
```

```
##  [1] "awk"         "bash"        "coffee"      "gawk"        "groovy"     
##  [6] "haskell"     "lein"        "mysql"       "node"        "octave"     
## [11] "perl"        "psql"        "Rscript"     "ruby"        "sas"        
## [16] "scala"       "sed"         "sh"          "stata"       "zsh"        
## [21] "highlight"   "Rcpp"        "tikz"        "dot"         "c"          
## [26] "fortran"     "fortran95"   "asy"         "cat"         "asis"       
## [31] "stan"        "block"       "block2"      "js"          "css"        
## [36] "sql"         "go"          "python"      "julia"       "sass"       
## [41] "scss"        "theorem"     "lemma"       "corollary"   "proposition"
## [46] "conjecture"  "definition"  "example"     "exercise"    "proof"      
## [51] "remark"      "solution"
```
