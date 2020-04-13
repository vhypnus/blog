# 定义

> When storage is allocated for a [variable](https://golang.org/ref/spec#Variables), either through a declaration or a call of `new`, or when a new value is created, either through a composite literal or a call of `make`, and no explicit initialization is provided, the variable or value is given a default value. Each element of such a variable or value is set to the *zero value* for its type: `false` for booleans, `0` for numeric types, `""` for strings, and **`nil` for pointers, functions, interfaces, slices, channels, and maps**. **This initialization is done recursively**, so for instance each element of an array of structs will have its fields zeroed if no value is specified.
>
> - 内存分配，显示分配new，make，隐式分配  ,递归初始化直到完成
> - **struct结构初始化并不是nil **，可以避免很好的避免很多非空校验，写过java代码的同学感悟应该很深夜





# 示例

```go
// 以下的结果都是一样的，a都会初始化为0
var a int 
var a = 0
var a  = new(int)
```



```go
// error case
/* 该定义有问题
type Node struct {
    Value int
    Next Node
}*/

// 以下在初始化时递归溢出，无限循环
// var node Node


type Node struct {
    Value int
    
    Next Node
}
```







