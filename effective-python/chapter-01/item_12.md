# 第12节：for和while循环之后避免使用else代码块

Python循环语句有一个其他绝大多数编程语言中都不支持的功能：你可以在一个循
环体后立即放置一个else代码块。

    ```python
    for i in range(3):
        print('Loop %d' % i)
    else:
        print('Else block!')
    ```

    >>>
    Loop 1
    Loop 2
    Loop 3
    Else block!

令人惊讶的是，else 代码块将会在循环结束时被立即执行。为什么这个子句（译者
注：把for/else看做一个复合语句，else 相当于子句）要被称之为 "else" ？而不
是 "and" ？在 if/else 语句中，else 表示“执行此代码块，假如此前的判断条件
不成立的话。” 在 try/except 语句中，except也有着同样的定义：“假如此前try
代码块尝试执行失败，就执行此代码块。”

类似的，try/except/else 中的 else 也遵循这个规则（参看第13节：利用好try/
except/else/finally 中的每个代码块），因为它表示“执行此代码块，如果之前的
代码块没有失败的话。”  try/finally 也是很直观的，它表示“执行完之前的尝试执
行的代码块后总是执行此代码块。”

给出Python中所有 else，except 和 finally 的用途，一个编程新手会假设 for/else
中 else 的含义是“假如循环没有完成则执行else代码块。” 实际上，它做着完全相反
的事。其实，在循环中使用了 break 语句是会跳过 else 代码块的。

    ```python
    for i in range(3):
        print('Loop %d' % i)
        if i==1:
            break
    else:
        print('Else block!')
    ```
    >>>
    Loop 0
    Loop 1

另一个意外之处是假如循环遍历一个空序列则 else 代码块会被立即执行。

    ```python
    for x in []:
        print('Never runs')
    else:
        print('For Else block!')
    ```
    >>>
    For Else block!

当while循环的初始条件为 false 时 else 代码块也会被执行。

    ```python
    while False:
        print('Never runs')
    else:
        print('While Else block!')
    ```
    >>>
    While Else block!

这些行为的理由是当你使用循环搜索一些东西的时候循环后的 else 代码块是有用的。
例如，你想证明两个数字是否互质（公因数只有1）。这里，我迭代遍历每一个可能的
公因数并测试这些数字。当尝试过每种可能之后，循环结束。当数字互质时 else 代码
块将被执行，因为循环并没有遇到 break 语句。

    ```python
    a = 4
    b = 9
    for i in range(2, min(a, b) + 1):
        print('Testing', i)
        if a % i == 0 and b % i == 0:
            print('Not coprime')
            break
    else:
        print('Coprime')
    ```
    >>>
    Testing 2
    Testing 3
    Testing 4
    Coprime

在实践中，你不应该按照这种方式编码。而是，你应该写一个辅助函数来做这个计算。
写这样的辅助函数有两种常见风格。

第一种方式是当你找到所需的条件时就及早返回。假如循环遍历失败，在循环外部返回
一个默认值。

    ```python
    def coprime(a, b):
        for i in range(2, min(a, b) + 1):
            if a % i == 0 and b % i ==0:
                return False
        return True
    ```

第二种方式是使用一个结果变量表示你在循环中是否找到了你要的。一旦你找到了就
使用 break 跳出循环。

    ```python
    def coprime2(a, b):
        is_coprime = True
        for i in range(2, min(a, b) + 1):
            if a % i == 0 and b % i ==0:
                is_coprime = False
                break
        return is_coprime
    ```

这两种方式对于阅读陌生代码的人来说都是很清晰的。你从 else 代码块获得的表达
性并没超过给将来想要理解你代码的人（包括你自己）所带来的负担。像循环这类简
单结构在 Python 中应该不言自明。你应该避免在循环体后使用 else 代码块。

# 要记住的事
  * Python 有特殊的语法允许在for和while循环后立即使用 else 代码块。
  * 循环体后的else 代码块只在循环体内不会遇到 break 语句时执行。
  * 避免在循环体后使用 else 代码块，因为它们的行为不直观且而容易混淆。
