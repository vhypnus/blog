```go
s := string([]byte{65,130}) 
fmt.Println(s) //output nothing
s  = string([]byte{65, 66, 67, 226, 130, 172})
fmt.Println(s) // ABC€
```

