- let it go
	- mom liked folding a certain way
- hear for the pain cry
	- otherwise let it go, let them play with each other
- beans in plastic bottles


https://jobs.siemens.com/en_US/externaljobs/JobDetail/490660?ste_sid=cf6bccb8d2d33ef700617dc5328f22c1

https://jobs.siemens.com/en_US/externaljobs/JobDetail/498504?ste_sid=cf6bccb8d2d33ef700617dc5328f22c1

https://www.google.com/about/careers/applications/jobs/results/124908209172292294-software-engineer-lll-site-reliability-engineering

- [ ] `#include <cstddef>`
	- [ ] `{cpp}std::size_t`
	- [ ] `{cpp}nullptr_t`
	- [ ] `{cpp}import std;`  C++20 and later
- [ ] `nullptr`, `NULL`, and `0`
- [ ] `{cpp}string`
	- [ ] Small String Optimization
	- [ ] always null-terminated `c_str()`
	- [ ] rich API
	- [ ] `{cpp}vector<char>`
		- [ ] copyable, assignable?
		- [ ] reallocation invalidates pointers/iterators?


## 1) Core identity and why people use C++

* [ ] **“Zero-cost abstractions” philosophy** (nice abstractions that compile away when used well)
* [ ] **C interoperability** (call C APIs, use OS APIs, embed/extend, link with legacy code)

## 2) The “daily bread” language mechanics

* [ ] **Strong static typing** (types checked at compile time)
* [ ] **Value semantics by default** (copy/move values; predictable local reasoning)
* [ ] **References and pointers** (two different “indirection tools” with different idioms)
* [x] **RAII (Resource Acquisition Is Initialization)** (tie resources to object lifetime)
* [ ] **Namespaces** (avoid symbol collisions)
* [ ] **Overloading** (functions/operators with the same name chosen by types)
* [ ] **Default arguments**
* [ ] **Templates** (generic code; compile-time polymorphism)
* [ ] **Exception handling** (try/throw/catch; with strong ecosystem conventions)
* [ ] **The preprocessor** (macros, includes, conditional compilation)

## 3) Modern C++ safety & expressiveness staples (C++11 → C++23-ish)

* [ ] **Move semantics** (`T&&`, move ctor/assign) to avoid copies
* [ ] **Smart pointers** `std::unique_ptr`, `std::shared_ptr`, `std::weak_ptr`
* [ ] **Type inference** (`auto`, `decltype`)
* [ ] **Range-based for**
* [ ] **Uniform initialization** (`{}` initialization; narrowing prevention in some cases)
* [ ] **Lambda expressions** (anonymous functions, captures)
* [ ] **`nullptr`** (real null pointer literal)
* [ ] **`constexpr` / compile-time evaluation** (from simple constants to full compile-time programs)
* [ ] **`enum class`** (scoped enums)
	* [ ] unscoped
	* [ ] stronger enum classes
* [ ] **Attributes** (`[[nodiscard]]`, `[[maybe_unused]]`, `[[likely]]`, etc.)
* [ ] **`static_assert`** (compile-time assertions)
* [ ] **Variadic templates** (generic code over parameter packs)
* [ ] **`noexcept`** (declare/enable optimizations & correctness constraints)
* [ ] **User-defined literals**
* [ ] **Structured bindings** (`auto [a,b] = ...;`)
* [ ] **`if constexpr`** (compile-time branching)
* [ ] **Class template argument deduction (CTAD)**
* [ ] **`std::optional`, `std::variant`, `std::any`** (sum/nullable/dynamic containers)
* [ ] **`std::string_view`** (non-owning string view)
* [ ] **`std::span`** (non-owning view over contiguous sequences)
* [ ] **`std::byte`** (byte-typed data)
* [ ] **`std::format`** (modern formatting)
* [ ] **`std::expected`** (C++23: value-or-error return type)

## 4) Object model & OOP features

* [ ] **Virtual functions & dynamic dispatch**
* [ ] **Abstract classes / interfaces (via pure virtual)**
* [ ] **`override` / `final`**
* [ ] **Object slicing** (important gotcha)
* [ ] **Polymorphic deletion** and **virtual destructors**
* [ ] **Friends** (friend functions/classes)
* [ ] **Nested types**
* [ ] **Access control & ADL interactions** (subtle, but common)

## 5) Generic programming superpowers

* [ ] **Function templates / class templates**
* [ ] **Template specialization** (full/partial)
* [ ] **SFINAE** (“substitution failure is not an error”)
* [ ] **Concepts** (C++20 constraints; `requires`)
* [ ] **`constexpr` templates / metaprogramming**
* [ ] **Type traits** (`<type_traits>`)
* [ ] **`std::tuple` and compile-time tuple tricks**
* [ ] **`std::invoke`, `std::apply`**
* [ ] **`std::function` vs templates** (type erasure vs static dispatch)
* [ ] **Policy-based design**
* [ ] **Expression templates** (advanced performance trick)

## 6) Standard library containers & strings (practical day-to-day)

* [ ] **`std::vector`** (workhorse dynamic array)
* [ ] **`std::string`**
* [ ] **`std::array`**
* [ ] **`std::deque`**
* [ ] **`std::list` / `std::forward_list`**
* [ ] **`std::map` / `std::set` (ordered tree)**
* [ ] **`std::unordered_map` / `std::unordered_set` (hash)**
* [ ] **`std::queue`, `std::stack`, `std::priority_queue`**
* [ ] **`std::bitset`**
* [ ] **`std::pmr::*` polymorphic allocators** (advanced perf/memory control)
* [ ] **Custom allocators** (powerful, often avoided unless needed)

## 7) Algorithms, iterators, ranges

* [ ] **Iterators** (the glue of the STL)
* [ ] **Algorithms library** (`sort`, `find`, `transform`, `accumulate`, etc.)
* [ ] **Comparator and projection patterns**
* [ ] **Ranges (C++20)** (`std::ranges`, views, pipelines
* [ ] **Iterator categories** (input/forward/bidirectional/random-access/contiguous)
* [ ] **Sentinels** (ranges end markers)
* [ ] **Lazy views** (`filter`, `transform`, `take`, etc.)

## 8) Concurrency & parallelism

* [ ] **Threads** `std::thread`
* [ ] **Mutexes / locks** `std::mutex`, `std::lock_guard`, `std::unique_lock`
* [ ] **Condition variables**
* [ ] **Atomics & memory ordering** (`std::atomic`, acquire/release/seq_cst
* [ ] **Futures/promises** (`std::future`, `std::promise`, `std::async`
* [ ] **`std::jthread`** (C++20: joining thread with stop token)
* [ ] **Stop tokens / cooperative cancellation**
* [ ] **Parallel algorithms** (`std::execution` policies — compiler/library dependent
* [ ] **Lock-free programming support** (atomics, fences; very advanced)

## 9) Error handling models (C++ is pluralistic)

* [ ] **Exceptions** (throw/catch; stack unwinding)
* [ ] **Error codes** (`std::error_code`, `std::system_error`
* [ ] **Optional/variant/expected** (return-based error handling)
* [ ] **Assertions** (`assert`, `static_assert`)
* [ ] **Contracts-ish via guidelines** (no official contracts yet in the standard)

## 10) Compilation model and tooling “features” that matter in practice

* [ ] **Separate compilation** (headers + translation units)
* [ ] **Linking model** (static/dynamic; ODR issues)
* [ ] **ABI concerns** (especially across compilers/standard libraries)
* [ ] **Header-only libraries** (template-heavy style)
* [ ] **Build systems** (CMake is the de facto standard)
* [ ] **Modules** (C++20: alternative to headers; still ecosystem-maturing)
* [ ] **Precompiled headers**
* [ ] **LTO / PGO** (link-time/profile-guided optimizations)

## 11) Memory management and object lifetime (deeply important)

* [ ] **Manual `new/delete`** (possible, but discouraged in modern style)
* [ ] **Ownership semantics** (unique/shared/borrowed)
* [ ] **Stack allocation** (cheap, deterministic)
* [ ] **Custom deleters**
* [ ] **Placement new**
* [ ] **Object lifetime rules** (very strict, sometimes surprising)
* [ ] **Aliasing rules / strict aliasing**
* [ ] **Alignment** (`alignas`, `std::align`
* [ ] **Allocator model** (containers parameterized by allocators)
* [ ] **Lifetime extension rules** (references, temporaries)
* [ ] **Copy elision / RVO** (can eliminate copies)

## 12) Type system depth

* [ ] **Const-correctness** (`const` everywhere; can be a superpower)
* [ ] **`mutable`** (escape hatch)
* [ ] **`volatile`** (not for threading; mostly MMIO / special cases)
* [ ] **Signed/unsigned & integer promotions**
* [ ] **Casts** (`static_cast`, `dynamic_cast`, `reinterpret_cast`, `const_cast`)
* [ ] **RTTI** (`typeid`, `dynamic_cast`)
* [ ] **Type erasure** patterns
* [ ] **`std::type_info`**
* [ ] **`decltype(auto)` return types**
* [ ] **Reference collapsing rules** (template + `T&&`)
* [ ] **CV/ref qualifiers**
* [ ] **`using` type aliases**
* [ ] **`typedef`** (legacy alias mechanism)

## 13) Low-level / systems features

* [ ] **Bit operations** (shifts, masks; `<bit>` utilities)
* [ ] **Control over layout** (`#pragma pack` in practice, `[[no_unique_address]]` etc.)
* [ ] **SIMD hooks** (compiler intrinsics; emerging std support)
* [ ] **Inline assembly** (compiler-specific)
* [ ] **Memory-mapped I/O patterns**
* [ ] **Endian awareness** (`std::endian` in `<bit>`)
* [ ] **`std::launder`** / obscure lifetime utilities (niche but real)

## 14) Metaprogramming and compile-time computation

* [ ] **Template metaprogramming** (types-as-values)
* [ ] **`constexpr` as a “real” compute substrate**
* [ ] **`consteval`** (must be evaluated at compile-time)
* [ ] **`constinit`** (forces constant initialization of globals)
* [ ] **Reflection** (not fully standardized yet; partial facilities exist but evolving)
* [ ] **Compile-time strings & structural types tricks**

## 15) Language integration and interop

* [ ] **C ABI (`extern "C"`)**
* [ ] **Name mangling and linkage**
* [ ] **FFI patterns to Python/Rust/etc.**
* [ ] **COM / Win32 / POSIX integration**
* [ ] **Embedding scripting languages**
* [ ] **Calling conventions** (platform/compiler specifics)

## 16) I/O and filesystem (standard library)

* [ ] **Streams** (`iostream`, `fstream`, formatting flags)
* [ ] **I/O manipulators**
* [ ] **`std::filesystem`** (paths, directory iteration, file ops)
* [ ] **Locales** (powerful, complex)
* [ ] **Sync with C stdio** (performance considerations)

## 17) Numeric, time, utilities

* [ ] **`<cmath>` and numeric utilities**
* [ ] **Random numbers** (`<random>` engines/distributions)
* [ ] **Chrono time library** (`std::chrono`, durations, clocks)
* [ ] **`std::ratio`** (compile-time rational numbers)
* [ ] **Complex numbers** (`std::complex`)
* [ ] **`std::valarray`** (legacy-ish numeric container)
* [ ] **`std::numeric_limits`**

## 18) Functional-ish and compositional tools

* [ ] **Higher-order functions via templates/lambdas**
* [ ] **`std::bind`** (older; mostly replaced by lambdas)
* [ ] **`std::function`** (type-erased callable)
* [ ] **Monadic patterns with `optional/expected`** (idioms, not built-in)

## 19) Newer “big ticket” additions people talk about

* [ ] **Coroutines (C++20)** (`co_await`, `co_yield`, `co_return`) — framework-driven
* [ ] **Modules (C++20)** — promises faster builds/cleaner boundaries (ecosystem still catching up)
* [ ] **Ranges (C++20)** — more expressive algorithm pipelines
* [ ] **Three-way comparison (C++20)** (`<=>`)
* [ ] **Designated initializers (C++20)** (limited compared to C)
* [ ] **`std::print` / `std::println`** (C++23; depends on lib support)

## 20) Subtle rules / “sharp edges” that are effectively part of C++

These are “features” in the sense that you *must* know they exist.

* [ ] **Undefined behavior (UB)** (performance enabler + footgun)
* [ ] **Unspecified / implementation-defined behavior**
* [ ] **One Definition Rule (ODR)**
* [ ] **Strict aliasing & effective type rules**
* [ ] **Integer overflow rules (signed overflow UB)**
* [ ] **Lifetime / dangling references**
* [ ] **Data races are UB** (without atomics/synchronization)
* [ ] **Order of evaluation pitfalls** (much improved over time, but still relevant)
* [ ] **Exception safety levels** (basic/strong/nothrow guarantees)
* [ ] **The rule of 0/3/5** (resource-managing types)

## 21) Language “surface area” features (misc but real)

* [ ] **Operator overloading**
* [ ] **User-defined conversions**
* [ ] **Explicit constructors / conversion operators (`explicit`)**
* [ ] **`friend`**
* [ ] **`inline` variables**
* [ ] **`static` storage and linkage**
* [ ] **`thread_local`**
* [ ] **`union`**
* [ ] **Bit-fields**
* [ ] **`goto`** (rare, but exists)
* [ ] **`switch` fallthrough attributes**
* [ ] **`decltype`, `sizeof`, `alignof`, `offsetof`**
* [ ] **`requires` expressions and requires-clauses**
* [ ] **`using enum` (C++20)**
* [ ] **`std::initializer_list`**

## 22) Standard library: “glue” utilities everybody eventually uses

* [ ] **`std::pair`**
* [ ] **`std::tuple`**
* [ ] **`std::swap`**
* [ ] **`std::move` / `std::forward`**
* [ ] **`std::reference_wrapper`**
* [ ] **`std::optional`**
* [ ] **`std::variant`**
* [ ] **`std::expected`**
* [ ] **`std::any`**
* [ ] **`std::unique_ptr` / `std::shared_ptr`**
* [ ] **`std::chrono` basics**
* [ ] **`std::span`, `std::string_view`**
* [ ] **`std::bit_cast`**
* [ ] **`std::source_location`**
* [ ] **`std::ranges` utilities**

## 23) Ecosystem-adjacent “features” people associate with C++

Not in the language, but effectively part of “C++ in real life”.

* [ ] **Compiler extensions** (attributes, pragmas, builtins, sanitizers)
* [ ] **Sanitizers** (ASan/UBSan/TSan)
* [ ] **Static analysis** (clang-tidy, cppcheck)
* [ ] **Formatting tooling** (`clang-format`)
* [ ] **Package managers** (vcpkg, Conan)
* [ ] **Testing frameworks** (Catch2, GoogleTest)
* [ ] **Benchmarking** (Google Benchmark)
* [ ] **Guidelines & profiles** (Core Guidelines, safety profiles in some orgs)

## 24) Domain-specific strengths (why the above matters)

* [ ] **Embedded/firmware** (no GC, deterministic lifetime, control)
* [ ] **Game engines** (performance, memory control, custom allocators, SIMD)
* [ ] **Realtime systems** (predictable behavior possible with discipline)
* [ ] **HPC** (templates + vectorization + threading + low-level control)
* [ ] **Interop-heavy apps** (C APIs everywhere)
* [ ] **Large-scale systems** (with modern practices and tooling)
