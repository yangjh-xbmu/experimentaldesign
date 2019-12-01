# 常用功能的实现 {#howtodo}

## 如何插入参考文献

1. 插入参考文献时，需要创建.bib格式的参考文献数据库。
2. 在合适的地方插入引用[@xie2015]，语法[@毛向樱2018]如下：

   ```
   引用[@xie2015]
   ```
3. 单独创建一个显示全部参考文献的.Rmd文件，内容如下：
   ```
   # References {-}
   ```

按照上述步骤，将在章节末尾和全书末尾生成参考文献。

## 如何将参考文献格式调整为国标格式

在首页文件`index.Rmd`中，用户可以通过`biblio-style`指定参考文献的格式，例如：

```yaml
---
bibliography: ["one.bib", "another.bib", "yet-another.bib"]
biblio-style: "GBT7714-2005"
link-citations: true
---
```

与此同时，还需要将上述文件复制到项目目录中，不过上述设定，仅对PDF和word输出时起作用，对于gitbook格式，则没有效果。
