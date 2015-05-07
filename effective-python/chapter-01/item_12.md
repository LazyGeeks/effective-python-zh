#第12节：for和while循环之后避免使用else代码块

Python循环语句有一个其他绝大多数编程语言中都不支持的功能：你可以在一个循
环体后立即放置一个else代码块。


    ```
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


令人惊讶的是，else代码块将会在循环结束时被立即执行。为什么这个子句（译者
注：把for/else看做一个复合语句，else相当于子句）要被称之为 "else" ？而不
是 "and" ？在 if/else 语句中，else 表示“执行此代码块，假如此前的判断条件
不成立的话。” 在 try/except 语句中，except也有着同样的定义：“假如此前try
代码块尝试执行失败，就执行此代码块。”


类似的，try/except/else 中的 else 也遵循这个规则（参看第13节：利用好try/
except/else/finally中的每个代码块），因为它表示“执行此代码块，如果之前的
代码块没有失败的话。” try/finally也是很直观的，它表示“执行完之前的尝试执
行的代码块后总是执行此代码块。”
