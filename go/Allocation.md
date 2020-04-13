# 定义

>  The built-in function `new` takes a type `T`, allocates storage for a [variable](https://golang.org/ref/spec#Variables) of that type at run time, and returns a value of type `*T` [pointing](https://golang.org/ref/spec#Pointer_types) to it. The variable is initialized as described in the section on [initial values](https://golang.org/ref/spec#The_zero_value).
>
> - 两种方式new





# Demo



```go
new(T)
```

For instance

```go
type S struct { a int; b float64 }
new(S)
// var v S 与new等价
```

allocates storage for a variable of type `S`, initializes it (`a=0`, `b=0.0`), and returns a value of type `*S` containing the address of the location.