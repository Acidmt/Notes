## vector

vector 是 C++ 标准库中的一个动态数组容器，它可以自动管理内存大小，可以在运行时根据需要动态增长或缩小。它是一个非常常用且强大的容器，用于存储一系列元素。下面详细介绍 `vector` 的使用方法，并提供相应的代码案例。

首先，使用需要引入头文件 `<vector>`。

```C
#include <vector>
```

直接使用 `vector` 模板类来创建一个 vector 对象。可以创建存储特定类型元素的 vector，格式为： `vector<数据类型> 名字`。例如：

```c
vector<int> myVector; // 创建一个存储整数的 vector，名字为myVector
vector<char> myVector; // 创建一个存储字符的 vector，名字为myVector
vector<string> myVector; // 创建一个存储字符串的 vector，名字为myVector
```

https://zhuanlan.zhihu.com/p/648650828

## map

Map是STL的一个关联容器，它提供一对一（其中第一个可以称为关键字，每个关键字只能在map中出现一次，第二个可能称为该关键字的值）的数据处理能力，由于这个特性，它完成有可能在我们处理一对一数据的时候，在编程上提供快速通道。这里说下map内部数据的组织，map内部自建一颗红黑树(一种非严格意义上的平衡二叉树)，这颗树具有对数据自动排序的功能，所以在map内部所有的数据都是有序的，后边我们会见识到有序的好处。