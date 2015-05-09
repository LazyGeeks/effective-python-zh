# 条款 01：了解你所使用的 Python 版本

在本书中，大部分示例代码都采用 Python 3.4（发布于 2014 年 3 月 17 日）的语法。为了强调一些重要的差异点，本书也会提供一些基于 Python 2.7（发布于 2010 年 7 月 3 日）语法的示例代码。对于所有流行的 Python 运行时环境：CPython、Jython、IronPython 和 PyPy 等等，我的大部分建议都是有效的。

在很多计算机上，都会预装多种版本的标准 CPython 运行时环境。但是，在命令行中，`python` 命令的默认含义可能并不清晰。`python` 通常是 `python2.7` 的别名，但有时也可能是更老的版本如 `python2.6` 或 `python2.7` 的别名。为了确定你正在使用的 Python 版本，你可以（在 `python` 命令后面）使用 `--version--` 标记。

```
$ python --version
Python 2.7.8
```

Python 3 对应的命令名通常是 `python3`。

```
$ python3 --version
Python 3.4.2
```

通过检查内建模块 `sys` 的属性值，你也能识别出你当前使用的 Python 版本。

```python
import sys
print(sys.version_info)
print(sys.version)
```

```
>>>
sys.version_info(major=3, minor=4, micro=2, releaselevel=‘final’, serial=0)
3.4.2 (default, Oct 19 2014, 17:52:17)
[GCC 4.2.1 Compatible Apple LLVM 6.0 (clang-600.0.51)]
```

Python 2 和 Python 3 都是 Python 社区在积极维护的版本。目前针对 Python 2 的开发主要集中在缺陷修复、安全性提升和有助于从 Python 2 迁移到 Python 3 的补丁（backports）等方面。辅助工具如 `2to3` 和 `six` 的存在都是为了让大家向 Python 3 迈进的步伐更轻盈些。

在 Python 3 中不断加入的新特性和改进将不会被加入到 Python 2 中。在本书撰写之时，Python 中最常用的开源库大部分都已经兼容 Python 3。我强烈建议你采用 Python 3 来开发你的下一个 Python 项目。



## 请记住

+ 有两个主要的 Python 版本仍在被广泛使用：Python 2 和 Python 3。
+ 存在多个流行的 Python 运行时环境：CPython、Jython、IronPython 和 PyPy 等等。
+ 确保在你的系统命令行中，你使用的是你预期的 Python 版本。
+ 优先选择 Python 3 来开发你的下一个项目，因为它是 Python 社区的主要关注点。
