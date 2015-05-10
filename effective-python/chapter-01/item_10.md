# 条款10：使用 enumerate 代替 range

内建函数 **range** 是循环迭代一个整数集合的有用函数。

```python
    random_bits = 0
    for i in range(64):
        if randint(0, 1):
            random_bits |= 1 << i
```

当你需要对一种数据结结构去迭代时，如一个字符串列表，你可以直接循环去处理这个序列。
如：

```python
flavor_list = ['vanilla', 'chocolate', 'pecan', strawberry']
for flavor in flavor_list:
   print(' %s is delicious' % flavor)
```

通常，在迭代一个列表同时，你也想得到当前元素的下标。例如你想要打印出你最喜欢的冰淇淋口味排序。使用 range 是其中一种方式。

```python
for i in range(len(flavor_list)):
	flavor = flavor_list[i]
	print('%d: %s' % (i + 1, flavor))
```

跟另一个使用 **range** 迭代遍历 `flavor_list` 的例子相比，这看起来很笨拙。你必须要得到列表的长度。你必须要索引这个列表。这变得难以阅读。

Python 提供了内建函数 **enumerate** 处理这种情况。**enumerate** 可以用一个简单的生成器包装任何可迭代对象。这个生成器返回一对包括循环下标和下标对应的值。下面这种代码看起来更简洁。

```python
for i flavor in enumerate(flavor_list):
    print('%d: %s' % (i + 1, flavor))
```

```
>>>
1: vanilla
2: chocolate
3: pecan
4: strawberry
```

你可以设置一个数字告诉 **enumerate** 从哪里开始计数（这个例子是从 1 开始）。

```python
for i flavor in enumerate(flavor_list, 1):
    print('%d: %s' % (i, flavor))
```

## 请记住
* **enumerate** 为循环遍历一个可迭代对象，获取该对象的每一个元素的下标提供了简洁的语法。
* 使用 **enumerate** 代替 **range** 循环遍历和索引一个序列。
* 你可以给　**enumerate** 提供一个整数作为第二个参数指定计数开始的数字（默认是0）。


