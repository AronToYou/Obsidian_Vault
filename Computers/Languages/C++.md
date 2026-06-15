
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