### zero value

### pointer

- the address of the variable
- ＆x means of the address of variable x 
- *x means of the value of variable x

### new

unnamed variable

### lifetime of variable

- package level
- the variable lives on until it becomes unreachablel,at which point its storage may be recycled
- function parameter and result are local variable too

### assignabiliy

- explicit or  implicitly

### comparability

### type declaration

- **name type** that has the same underlying type as an existing type
- Type declaration most often appear at package level,where the name type is visible through out the package,and if the name is exported(it starts with an **upper case letter**),it is acceible from other package as well

```go
type name underlying-type
```

 **example**

```go
# example
import "fmt"

type Celsius float64

const(
	FreezingC Celsius = 0
)
```



### Conversion

- for every type T ,  there is a corresponding conversion operations T(x), that convert the value x to type T.
- A conversion from one type to another is allow if 

1. both have the same underlying type 
2. both are unnamed pointer types that point to variables of the same underlying typ

- conversion change the type but not change the value

### scope

scope vs lifetime



### strings

- is an immutable sequence of bytes



