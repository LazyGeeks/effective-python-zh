# Markdown 规范

完整的 **Markdown 语法** 参考 [Markdown Here Cheatsheet][1]。


为了统一风格，请大家一起遵循以下规范：


## 间隔

*标题*、*底部链接* 与正文之间，保持 **两个空行** 的间隔。


## 标题

采用：

    # H1
    ## H2
    ### H3
    #### H4
    ##### H5
    ###### H6

避免：

    Alt-H1
    ======

    Alt-H2
    ------


## 链接

采用：

    [Some text][1]

    [1]: http://example.com/some-text

避免：

    [Some text](http://example.com/some-text)

**备注**：*书籍目录*，以及 *文档之间的相互链接* 等除外。


## 图片

采用：

    ![Alt text](http://image.com/sample)

避免：

    ![Alt text][logo]

    [logo]: http://image.com/sample

**备注**：有意与 [链接](#链接) 作区分。


## 代码块

采用：

    ```javascript
    var s = "JavaScript syntax highlighting";
    alert(s);
    ```

    ```python
    s = "Python syntax highlighting"
    print s
    ```

    ```
    No language indicated, so no syntax highlighting.
    But let's throw in a <b>tag</b>.
    ```


## 表格

采用：

```
Tables        | Are           | Cool
------------- |:-------------:| -----:
col 3 is      | right-aligned | $1600
col 2 is      | centered      |   $12
zebra stripes | are neat      |    $1
```

避免：

```
Tables | Are | Cool
--- |:---:| ---:
col 3 is | right-aligned | $1600
col 2 is | centered | $12
zebra stripes | are neat | $1
```

或

```
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |
```


[1]: https://github.com/adam-p/markdown-here/wiki/Markdown-Here-Cheatsheet
