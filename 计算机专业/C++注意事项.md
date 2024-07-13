# new关键字

~~~c++
l=(liStack)new liStack;
~~~

$new$关键字返回值是类型指针，如果这里$l$是地址，则需要进行强制类型转换。

# 结构体中的指针

~~~c++
typedef struct sqStack{
	char *data;
	struct sqStack *next;
}LNode,*liStack;
~~~

这里的$data$要想赋值需要每次都申请空间。如：

~~~c++
l->data=new char;
*(l->data)=e;
~~~

另外上面的`LNode`和`*liStack`代表意义一样，是给`typedef struct sqStack`起了两个别名。其中的`liStack`声明的变量是指针类型。

