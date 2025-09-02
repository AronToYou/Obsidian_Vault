---
created: 2024-01-31 10:09:21Z
---

# Performance Tips
- `if` statements are much faster than `try-except` blocks, *if* many exceptions are triggered
- "Loop Optimization" by setting `read_f = f.read`, then using `read_f` in a looped operation
- [Counting lines of a file efficiently](../../Computers/Python/I_O.md#efficient-line-counting)
- `iter(partial(f.read, 64), b'')`  is slower for line reading
	- look [here](https://docs.python.org/3/library/functions.html#iter)
- [assignment expressions](https://peps.python.org/pep-0572/) do not seam to slow down performance


# Readings
- [__future__ statements](https://docs.python.org/3/library/__future__.html)
- [WebAssembly compatibility](https://docs.python.org/3/library/intro.html#wasm-availability)
- [mmap](https://docs.python.org/3/library/mmap.html)