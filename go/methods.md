```go
package geometry
import "math"
type Point struct{ X, Y float64 }
// traditional function
func Distance(p, q Point) float64 {
	return math.Hypot(q.X-p.X, q.Y-p.Y)
}
// same thing, but as a method of the Point type
func (p Point) Distance(q Point) float64 {
	return math.Hypot(q.X-p.X, q.Y-p.Y)
}



p := Point{1, 2}
q := Point{4, 6}
fmt.Println(Distance(p, q)) // "5", function call
fmt.Println(p.Distance(q)) // "5", method call
```





### receiver

sending a message to an object



### method with a Pointer Receiver

because calling a functiion makes a copy of each argument value,if a function needs to update a variable,or if an argument is so large that we wish  to avoid copying it ,we nust pass the address of the variable using a pointer.



### Nil is a valid receiver value