

```go
type Sample struct {
	val int
}

func main(){
	var v = &Sample{16}

	fmt.Println(v)

	test(v)

	fmt.Println(v)
}

func test(v interface{}) {
	var s = v.(*Sample)
	s.val = 20
}
```

