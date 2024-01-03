## 字符串

|  字符串方法  |                   作用                   |            实现            |
| :----------: | :--------------------------------------: | :------------------------: |
|    find()    |   查找字符串是否包含子串，不存在返回-1   |       str.find('t')        |
|  replace()   |      替换指定字符串，返回新的字符串      | str.replace(old,new,次数)  |
|   split()    | 按照指定分隔符对字符串进行分割，返回列表 | str.split(分隔符,分割次数) |
|   strip()    |      移除字符串尾部和头部的指定字符      |     str.strip([chars])     |
|   lstrip()   |          移除字符串左侧指定字符          |    str.lstrip([chars])     |
|   rstrip()   |          移除字符串右侧指定字符          |    str.rstrip([chars])     |
|   upper()    |        将字符串中的小写转换为大写        |        str.upper()         |
|   lower()    |        将字符串中的大写转换为小写        |        str.lower()         |
| capitalize() |       将字符串第一个字母转换为大写       |      str.capitalize()      |
|   title()    |     将字符串每个单词首字母转换为大写     |        str.title()         |

## 列表

|          方法           |                作用                |           实现            |
| :---------------------: | :--------------------------------: | :-----------------------: |
|         list()          |              创建列表              |      list(range(20))      |
|      [n`:m`:step]       |          切片，包头不包尾          |                           |
| isinstance(ls,Iterable) |        判断ls是不是迭代对象        |                           |
|        append()         |       再列表末尾添加新的元素       |       list.append()       |
|        extend()         |   一次性追加另一个列表的所有元素   |    list.extend(list2)     |
|        insert()         |          按照索引位置插入          |    list.insert(2,'A')     |
|         sord()          |          默认按照升序排序          | list.sord([reverse=True]) |
|         sored()         |            产生新的列表            |                           |
|        reverse()        |              列表逆置              |                           |
|         del语句         |    删除指定位置或这个列表的元素    |   del list/del list[2]    |
|        remove()         |     移除指定元素，只移除第一个     |     list.remove('2')      |
|          pop()          | 移除指定下标元素，默认移除最后一个 |   list.pop/list.pop(1)    |

## 元组

|  方法   |   作用   |        实现        |
| :-----: | :------: | :----------------: |
| tuple() | 创建元组 | t1=tuple(range(5)) |

## 集合

|     方法      |                     作用                      |       实现        |
| :-----------: | :-------------------------------------------: | :---------------: |
|     set()     |                   创建集合                    |      s=set()      |
|     add()     |       像集合添加指定元素，存在则不添加        |      add(x)       |
|   remove(x)   |                删除集合中元素x                |                   |
|  discard(x)   |        删除集合中元素x，不存在不会报错        |                   |
|     pop()     |       随即删除一个元素，集合为空则报错        |                   |
|    clear()    |                   清空集合                    |     s.clear()     |
|    copy()     |                   复制集合                    |   s1=s2.copy()    |
| isdisjoint(T) | 判断集合与集合T是否没有相同元素，没有返会True | s1.isdisjoint(s2) |

## 字典

|   方法    |          作用          |                     实现                      |
| :-------: | :--------------------: | :-------------------------------------------: |
|  dict()   |        创建字典        |                 d=dict{'A':1}                 |
|   get()   |      根据键得到值      |                  d.get('A')                   |
| update()  |     添加和修改元素     | 添加：d.update(B=12)<br/>修改：d.update(A=12) |
|   pop()   | 根据指定键删除对应元素 |                  d.pop('A')                   |
| popitem() |    随机删除字典元素    |                                               |
|  clear()  |        清空字典        |                   d.clear()                   |

~~~python
#字典推导式
{key:value for key,value in d}
#列表推导式
[i for i in list]
~~~

