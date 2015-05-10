# 使用 zip 并行处理可迭代对象

在 Python 中，你。通过在列表解析运用表达式可以很容易处理一个源列表，得到一个衍生的列表。

```python
name = ['Cecilia', 'lise', 'Marie']
letters = [len(n) for n in names]
```

衍生列表的元素和源列表的元素通过下标关联。为了并行处理 2 个列表，你可以迭代次数 **names** 源列表的长度。

```python
longest_name = None
max_letters = 0

for i in range(len(names)):
    count = letters[i]
    if count > max_letters:
        longest_name = names[i]
        max_letters = count

print(longest_name)
```

```
>>>
Cecilia
```

这样的话问题在于整个循环在阅读上很复杂。**names** 和 **letters** 的索引让代码变得难以阅读。通过循环索引 i 来索引列表会发生2次。使用 **enumerate** 稍微优化一下这段代码。

```python
for i, name in enumerate(names):
    count = letters[i]
    if count > max_letters:
        longest_name = names
        max_letters = count
```

为了让这段代码更简洁，Python 提供了 **zip** 内建函数。在 Python 3，**zip** 用一个简单的生成器包装2个或多个可迭代对象。**zip** 生成器抛出一个包含每个可迭代对象元素值的元组。下面的代码比同时索引2个列表更简洁。

```python
for name, count in zip(names, letters):
	if count > max_letters:
	longest_name = name
	max_letters = count
```

不过内建函数 **zip** 有 2 个问题。
第一是在 Python 2 里面 **zip** 不是一个生成器。它会遍历完提供的可迭代对象，返回一个包含 **zip** 生成所有的元组的列表。这会潜在地使用大量的内存，导致你的程序崩溃。如果你想使用 **zip** 处理一个巨大的可迭代对象，你可以使用内置模块 **itertools** 的 **izip** 。
第二个问题是如果输入的可迭代对象的长度不同，**zip** 会表现得奇怪。例如，你向上面的列表 **names** 添加另一个名字，但是忘记更新 **letters**。用 **zip** 处理 2 个列表会得到意外的结果。

```python
names.append('Rosalind')
for name, count in zip(names, lettres):
    print(name)
```

```
>>>
Cecilia
Lise
Marie
```

新元素 **Rosalind** 并不在里面。**zip** 就是这样工作的。它不断的抛出元组直到其中一个可迭代对象结束。当你知道 2 个可迭代对象长度相同，通常是由其中一个列表解析衍生出另一个列表这种情况，**zip** 这种处理方法会很好用。但是在很多情况下，**zip** 这种会截断其中某一个列表的行为是令人吃惊和不好的。如果你不确认 **zip** 处理的列表长度是否相等，考虑使用内置模块 **itertools** 的 **zip_longest** 方法替代。

# 请记住
* 内建函数 **zip** 是用来并行迭代多个可迭代对象的。
* 在 Python 3，**zip**是一个生成元组的生成器。在 Python 2，**zip** 返回的是一个包含所有元组的列表。
* 如果你提供的可迭代对象的长度不相等，**zip** 会悄无声息的截断输出。
* 内建模块 **itertools** 的 **zip_longest** 函数可以在并行迭代多个可迭代对象让你忽略它们的长度。
