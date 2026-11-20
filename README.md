# OS Storage Management System (x86 Assembly)

Low-level implementation of a contiguous block storage manager written in 32-bit x86 Assembly (AT&T syntax). Built for the Computer Systems Architecture (ASC) course at the Faculty of Mathematics and Computer Science, University of Bucharest.

The program simulates file allocation, lookup, deletion, and compaction on a fixed-size block device, supporting both unidimensional (1D) and bidimensional (2D) memory layouts.

## Storage Models & Constraints

- **Block Granularity:** Each storage block represents `8 KB`.
- **1D Linear Layout:** `8 MB` total capacity partitioned into `1,024` contiguous blocks (`0` to `1023`).
- **2D Matrix Layout:** `1,024 x 1,024` grid of `8 KB` blocks (`8 MB x 8 MB` address space). Files must fit contiguously within a single row without wrapping across lines.
- **File Descriptors:** Integer IDs in the range `1..255` (`0` denotes a free block).
- **Minimum Allocation:** Every file occupies at least `2` blocks (`ceil(size_kb / 8)`).
- **Allocation Strategy:** First-fit search scanning from index `0` (top-left in 2D) for the first contiguous free interval large enough to hold the file.

## Supported Operations

- **`ADD`** — Reads a file descriptor and size in KB, computes the required block count, and allocates the first available contiguous interval. Outputs the allocated start/end indices (or `(0, 0)` if insufficient contiguous space exists).
- **`GET`** — Searches storage for a given descriptor and prints its start and end block coordinates, or `(0, 0)` if the descriptor is not present.
- **`DELETE`** — Locates all blocks belonging to a given descriptor and resets them to `0`, then prints the updated intervals of remaining files.
- **`DEFRAGMENTATION`** — Compacts all allocated files toward the beginning of the storage space to eliminate external fragmentation while preserving relative file order and row-level contiguity (in 2D mode).
- **`CONCRETE` (2D only)** — Accepts an absolute directory path, traverses its entries using Linux system calls, extracts each file's descriptor (`fd % 256`) and size in KB from file metadata, and allocates them into the 2D storage grid.

## Build & Run

Requires a Linux environment with 32-bit compilation support (`gcc-multilib`).

### 1. Compile (32-bit x86)
```bash
gcc -m32 -no-pie task_1d.s -o task_1d
gcc -m32 -no-pie task_2d.s -o task_2d
