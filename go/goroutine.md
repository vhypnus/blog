```go
func main(){

	var ch = make(chan int)
	ch <- 123

	fmt.Println("hello world")
}

----------------------------output

fatal error: all goroutines are asleep - deadlock!

goroutine 1 [chan send]:

```



```go
func main(){
	var ch = make(chan int)

	go func(){
		fmt.Println("step 1")
		var v = <- ch
		fmt.Println("step 2 %v",v)
	}()

	time.Sleep(4*time.Second)
	fmt.Println("wake up")
}


-----------------------------output
> Output:
command-line-arguments
step 1
wake up
> Elapsed: 4.888s
> Result: Success
```





### 非阻塞



```go
func main(){
	var ch = make(chan int)

	go func(){
		select { 
			case v := <- ch:
				fmt.Printf("value of :%v",v)
             case <- time.After(time.Second):
            	 fmt.Println("i am timeout")
			default:
				fmt.Println("hello world")
		}
		fmt.Println("iamout")
	}()

	time.Sleep(4*time.Second)
	fmt.Println("wake up...")
}

--------------------------output
> Output:
command-line-arguments
hello world
iamout
wake up...
> Elapsed: 4.867s
> Result: Success
```



```go
func main(){
	var ch = make(chan int)

	go func(){
		select {
			case v := <- ch:
				fmt.Printf("value of :%v",v)
			case <- time.After(time.Second):
				fmt.Println("i am timeout")
		}
		fmt.Println("iamout")
	}()

	time.Sleep(4*time.Second)
	fmt.Println("wake up...")
}

------------------------------------------output
> Output:
i am timeout
iamout
wake up...
> Elapsed: 4.813s
> Result: Success
```

