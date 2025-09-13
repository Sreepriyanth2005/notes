
### DMA?
**Dynamic Memory Allocation (DMA)** allows your program to **request memory at runtime** instead of compile time.

- Memory is taken from the **heap** (dynamic memory area).
- You can **allocate**, **resize**, and **free** memory while your program is running.
- You can **create arrays, structures, or buffers** whose size depends on user input or runtime conditions.

### Why DMA?

- **Variable size data:** e.g., reading `n` numbers where `n` is known only at runtime.
- **Efficient memory usage:** allocate memory only when needed.
- **Flexible data structures:** linked lists, trees, graphs, hash tables.

### Functions in DMA

C provides 4 main functions in `<stdlib.h>`:

| Function    | Purpose                                 |
| ----------- | --------------------------------------- |
| `malloc()`  | Allocates **uninitialized** memory      |
| `calloc()`  | Allocates **zero-initialized** memory   |
| `realloc()` | **Resizes** previously allocated memory |
| `free()`    | **Releases** allocated memory           |
##### malloc()

```c
void* malloc(size_t size);
```

- Allocates **size bytes** in heap.
- Returns a **void pointer** to the allocated memory.
- **Memory is uninitialized** (contains garbage values).
###### Example

```c
int *arr = (int*)malloc(n * sizeof(int));
```

##### calloc()

```c
void* calloc(size_t num, size_t size);
```

- Allocates memory for **num elements**, each of **size bytes**.
- **Initializes all bytes to 0**.
###### Example

```c
int *arr = (int*)calloc(n, sizeof(int));
```

##### relloc()

```c
void* realloc(void* ptr, size_t new_size);
```

- **Resizes** memory block allocated by `malloc()` or `calloc()`.
- Preserves existing data (up to smaller of old/new size).
- Woking Internally:
	- `realloc()` **resizes in the same place** → pointer remains same.
	- Allocates **new memory block in heap**
	- **Copies old data** to new block
	- **Frees old block internally**
	- Returns **new pointer** (different address)
###### Example:

```c
arr = (int*)realloc(arr, 2*n * sizeof(int));
```

##### free()

```c
void free(void* ptr);
```

- **Frees allocated memory**, returning it to the heap.
- **Does not set pointer to NULL automatically.**
- Accessing freed memory = **undefined behavior (dangling pointer)**.
###### Example (Be)

```c
free(ptr);
ptr=NULL;
```