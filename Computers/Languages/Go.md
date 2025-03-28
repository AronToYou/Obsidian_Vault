# Declarations
```go
var x int64 = 5  // full

func main() {
	y := x + 5  // short declaration
}
```
- **short declarations** : can only be used within a **block**
	- overrides any declarations from outside the **block** while inside
	- when used in a loop, allocates memory everytime **BAD**

```go
var nums [3]int{0, 0, 0}  // array
var p []int = num[1:2]  // slice
s := []int{  // slices can hold anything
	[]int{0, 0, 0},
	[]int{0, 0, 0},
	[]int{0, 0, 0},
}
a := make([]int, 6)

// Structs
type Vector struct {  // struct
	x, y, z int
}

v := Vector{1, z:2}
v.x

// Maps
var m1 map[string]Vector
m1 = make(map[string]Vector)
var m2 = map[string]Vector{
	"test": Vector{1, 2, 3},
	"good": {3, 2, 1},  // only if top-level type is a type name
}

```

# Functions
```go
func adder() func(int) int {
	return func(x int) int {
		return 5
	}
}

func main() {
	f := adder()
}

// Struct Methods
type Vector struct {  // struct
	X, Y int
}

func (v Vector) Abs() int {  // cannot alter v.X
	return v.X
}
func (v *Vector) Rot() {
	v.X = 5
}
```

# Interfaces
```go
type Case interface {
	Abs() int
}

var c Case
v := Vector{1, 2}
c = &v  // v alone doesn't implement Abs
c = v  // panic
c = o  // Other type

// also
type Other int
func (o Other) Abs() int {
	return o
}

// Type assertion
var i interface{} = "fdsad"

s := i.(string)
s, ok := i.(int)
d = i.(int)  // panic

switch v := i.(type) {
	case int:
		do()
	case string:
		do()
	default:
}

// Stringers
type Stringer interface {  // fmt.Println(str)
	String() string
}
// error
type error interface {
	Error() string
}
// io.Reader
func (T) Read(b []byte) (n int, err error)

type customReader struct {
	r io.Reader
}
```