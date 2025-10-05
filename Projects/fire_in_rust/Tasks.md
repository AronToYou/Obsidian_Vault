- [x] replace `Vec` with `[]` ✅ 2025-09-14
	- [x] `Box<[[f32; NY]; NX]>` ✅ 2025-09-14
- [x] P convertible between `usize` & `f32` ✅ 2025-09-15
- [ ] Write down equations for ghost
- [ ] print rows

## Directions
- Field trait
	- apply trait to all field objects or special Field type
	- bilinear sample implemented for trait/type
- Rust Obsidian Vault within repo
	- README linked to main page in book
- Where to define min
	- in clamp
	- in `P<T>`
- Where to define clamp
	- in `Sim` method
	- in closure field

## Other

- [ ] trait of indexing
- [ ] trait of printing
- [x] const clamp impl ✅ 2025-09-14
- [ ] stack too much Sim

- [ ] generalize to 3D
- [ ] generic Field type
- [ ] somehow include physics package
- [ ] add smoke density
	- [ ] density dependent [gravity force](https://www.researchgate.net/publication/2390581_Visual_Simulation_of_Smoke)