# 定义

A pointer type denotes the set of all pointers to [variables](https://golang.org/ref/spec#Variables) of a given type, called the *base type* of the pointer. **The value of an uninitialized pointer is `nil`.**

```
PointerType = "*" BaseType .
BaseType    = Type .
```

示例

```go
*Point
*[4]int
```



```go
// raise error
// var a *Sample
// a = new(Node)
```

