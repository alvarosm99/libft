# 📚 Libft - 42 School

> *My very first own library, containing the building blocks for future C projects in 42 School.*

## 💡 About The Project

**Libft** (Library of functions) is the first project of the 42 School common core. The goal is to recreate standard C library functions (from `<string.h>`, `<ctype.h>`, `<stdlib.h>`) along with additional utility functions that will be used throughout the rest of the curriculum. 

By rewriting these functions from scratch, this project provides a deep understanding of memory allocation, pointer arithmetic, data structures, and the internal workings of standard C functions that are usually taken for granted.

---

## 🧠 Deep Dive: Core Concepts Explored

### 1. Memory Management & Pointers
In C, memory is not managed automatically. Libft forces a rigorous approach to memory allocation and safety:
*   **Dynamic Allocation (`malloc`, `free`):** Functions like `ft_split`, `ft_strjoin`, and `ft_itoa` require precise dynamic memory allocation. You learn to allocate exactly what is needed (including the null terminator `\0`) and free it appropriately to avoid memory leaks.
*   **Memory Manipulation:** Functions like `ft_memset`, `ft_memcpy`, `ft_memmove`, and `ft_bzero` require raw memory byte-by-byte manipulation using `unsigned char` pointers, teaching how memory contiguous blocks are structured and accessed safely without buffer overflows.
*   **Overlapping Memory:** `ft_memmove` specifically tackles the challenge of overlapping memory blocks, requiring conditional logic to copy from front-to-back or back-to-front depending on pointer addresses.

### 2. Struct Implementation & Linked Lists (Bonus)
The bonus part of the project introduces dynamic data structures through the implementation of Singly Linked Lists.
```c
typedef struct s_list
{
    void            *content;
    struct s_list   *next;
} t_list;
```

*  **Void Pointers (void \*):** The content variable is a void pointer, meaning the linked list is polymorphic and can store any data type (strings, integers, other structs). This teaches typecasting and generic programming in C.

*  **Node Linking & Traversal:** Functions like ft_lstadd_back and ft_lstmap teach how to traverse dynamic structures, link disjointed memory nodes, and safely apply function pointers across an entire dataset.

### 3. Bitwise Operations & Data Swapping

While the standard library deals heavily with characters and strings, underlying optimizations often require bit-level understanding:
*  **Bit Swapping:** Swapping data efficiently is a core algorithmic concept. While standard swaps use a temporary variable, bitwise XOR swaps `(a ^= b; b ^= a; a ^= b;)` can be implemented in custom utility functions to swap values at the register level without allocating extra memory.

*  **Bit Shifting & Masking:** Understanding ASCII values for ft_toupper or ft_tolower can be optimized using bitwise operations (e.g., flipping the 6th bit to switch between uppercase and lowercase letters).

---

## 🛠️ Function Overview
### Part 1 - Libc Functions

Re-implementations of standard C library functions:
*  **Memory:** `ft_memset`, `ft_bzero`, `ft_memcpy`, `ft_memmove`, `ft_memchr`, `ft_memcmp`, `ft_calloc`.
*  **String/Char:** `ft_strlen`, `ft_strlcpy`, `ft_strlcat`, `ft_strchr`, `ft_strrchr`, `ft_strncmp`, `ft_strnstr`, `ft_strdup`.
*  **Type verification:** `ft_isalpha`, `ft_isdigit`, `ft_isalnum`, `ft_isascii`, `ft_isprint`.
*  **Transformation:** `ft_toupper`, `ft_tolower`, `ft_atoi`.

### Part 2 - Additional Functions

Functions that are not part of the standard libc but are extremely useful for future projects:
*  **String Manipulation:** `ft_substr`, `ft_strjoin`, `ft_strtrim`, `ft_split`, `ft_strmapi`, `ft_striteri`.
*  **Conversion:** `ft_itoa`.
*  **File Descriptors (I/O):** `ft_putchar_fd`, `ft_putstr_fd`, `ft_putendl_fd`, `ft_putnbr_fd`.

### Bonus Part - Linked Lists
Functions to manipulate the t_list struct:

`ft_lstnew`, `ft_lstadd_front`, `ft_lstsize`, `ft_lstlast`, `ft_lstadd_back`, `ft_lstdelone`, `ft_lstclear`, `ft_lstiter`, `ft_lstmap`.

---

## 🚀 Compilation & Usage
This project includes a Makefile that compiles the source files into a static library (libft.a).
### Instructions
1. Clone the repository:
```Bash
git clone [https://github.com/your-username/libft.git](https://github.com/your-username/libft.git)
cd libft
```

2. Compile the library:
```Bash
make
```

This will generate the `libft.a` file.

3. Compile with bonus functions (Linked Lists):
```Bash
make bonus
```

4. Clean up object files:
```Bash
make clean
```

5. Clean up all generated files (objects and library):
```Bash
make fclean
```
---

## Using it in your projects

To use libft in your future C projects, include the header file in your C files:
```C
#include "libft.h"
```

And compile your project with the library:
```Bash
gcc -Wall -Wextra -Werror your_file.c -L. -lft
```
