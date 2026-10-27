- [ ] how again to manage pointers
	- [ ] how to do it with smart pointers
	- [ ] `std::lock_guard`
- [ ] Compiler directives
	- [ ] `#ifdef _WIN32`
	- [ ] barriers
		- [ ] lock free programs
- [ ] `std::move` - convert to `rvalue` category
	- [ ] `lvalue`s and `rvalue`s
	- [ ] `static_cast<T&&>(obj)`
- [ ] POSIX sockets
- [ ] copy elision
	- [ ] Return Value Optimisation
	- [ ] Named Return Value Optimisation
- [ ] alternatives to X-Lists
- [ ] Sphinx or Doxygen
	- [ ] how to format comments

## Topic Lists
- Performance
	- profile it
	- inspect flame graphs
	- identify hotspots
	- suggest vectorization
	- compare STL containers
	- benchmark alternatives
	- generate graphs
	- summarize findings
- testing
	- normal cases
	- edge cases
	- invalid input
	- fuzz tests
	- randomized tests
	- benchmark tests
	- v-model
		- unit tests
		- integration tests
		- installation -> end-to-end tests
# Versions
## C++11
- `std::move`
- `std::forward`
	- perfect forwarding
	- forwards not only value but type
```cpp
int& z = y;
void f(int x)
{
    g(x);
}
f(z) -> g((int)z)
```
## C++14

## Classes
### Initializer Lists
- execute before constructor
- more efficient
- required for
	- `{cpp}const`
	- references
```cpp
class my_object
{
	char* cstr;
	
public:
	my_object(const char* s = "") : cstr(nullptr) { }
	
	// I. Desctructor //
	~my_object() { delete[] cstr; }
	
	// II. Copy Constructor //
	my_object(const my_object& other) : my_object(other.cstr) {}
	
	// III. Copy Assignment //
	my_object& operator=(const my_object& other)
	{
		my_object temp_obj(other);
		std::swap(cstr, temp_obj.cstr);
		return *this;
	}
}
```
## Standard Library
- C library
	- `{cpp}<cstring>`
		- `{cpp}strcpy`
		- `{cpp}strncpy`
		- `{cpp}strlen`
		- `{cpp}string`
			- `{cpp}c_str`
			- `{cpp}size`
	- `{cpp}<iostream>`
		- `{cpp}cout`
		- `{cpp}cin`
	- `{cpp}<cstddef>`
		- `{cpp}size_t`
		- `{cpp}nullptr_t`
- Multi-Threading
	- `{cpp}<atomic>`
- Other
	- `{cpp}<utility>`
		- `{cpp}swap`
	- `{cpp}<algorithm>`
		- `{cpp}copy`
## Character Arrays
- pointers
	- `{cpp}char cstr[10];  // Stack`
	- `{cpp}char* cstr = new cstr[10];  // Heap`
	- `{cpp} std::unique_ptr<char[]>  // Smart`
- containers
	- `{cpp}std::array<char, 10> arr;  // Fixed`
	- `{cpp}std::vector<char> vec;  // Dynamic`
	- `{cpp}std::string s = "Yay";  // Modern`
> [!NOTE]-
> ```cpp
> using namespace std
> 
> char buf[10];  // stack pointer
> char buf[] = "initialized";
> char* cstring = new char[10];  // heap pointer
> // sizeof()
> 
> // Ownership
> unique_ptr<char[]> ustring;  // RAII pointer
> 
> array<char, 10> arr;  // Fixed size thin wrapper
> //.size(), .at()
> //copyable, assignable
> //STL algorithms
> 
> vector<char> vec; // Dynamically sized
> //contiguous memory!
> //.size(), .at()
> //STL algorithms
> ```

## Keywords
- `{cpp}explicit class`
	- prevents implicit conversions
		- e.g. single argument constructors


## Libraries
- Eigen
- Boost
- Ceres
- ROS
- OpenCV
- PCL