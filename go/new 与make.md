# 概述

内存申请通过new和make

**new**

-  并不做初始化
- 返回指针

**make**

- make 有专门的指定用途，初用于slice与map
- 并不返回指针



# 示例

## new

```go
	var x = new(string)
	fmt.Println(*x)  //output a address

	var i = new(int)
	fmt.Println(*i) //output a 
```

