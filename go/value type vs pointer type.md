



```go
type Sample struct {
	val int
}


func main(){
	var s1 = &Sample{17}
	var s2 = &Sample{17}
	var s3 = s2

	var m = make(map[*Sample]*Sample)
	m[s1] = s1
	m[s2] = s2
	fmt.Println(s2 == s3) // true
    fmt.Println(*s1 ==  *s2)//true
    fmt.Println(s1 == s2) //false
    fmt.Println(m[s3]) 
    fmt.Println(m[s1])
    fmt.Println(m[s2])

    s2.val = 18
	fmt.Println(s2 == s3) // true
    fmt.Println(*s1 ==  *s2)//false
    fmt.Println(s1 == s2) //false
    fmt.Println(m[s3]) //&{18}
    fmt.Println(m[s1])
    fmt.Println(m[s2])    
} 
```

