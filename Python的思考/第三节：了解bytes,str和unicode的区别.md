## 第三节：了解bytes,str和unicode的区别
* 在Python3中，有两种代表字符序列的类型：types和str。bytes的实例包含原始的8-bit值。str的实例包含Unicode字符。
* 在Python2中，有两种代表字符序列的类型：str和unicode。与Python3相比，str的实例包含原始的8-bit值。unicode的实例包含Unicode字符。
* 有很多方式来表示Unicode字符作为二进制数（原始的8-bit数）。最常见的编码方式就是UTF-8。重要的是，Python3中的str实例和Python2中的Unicode实例没有关于关联的二进制编码。把Unicode字符转化为二进制数，你必须使用encode方法。把二进制数转化为Unicode字符，你必须使用decode方法。
* 
