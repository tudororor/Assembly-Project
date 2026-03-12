# Assembly-Project

# Minimal OS Storage Management System (x86 Assembly)

## 📌 Project Overview
This project is a low-level implementation of a **storage management component** for a minimal operating system. [cite_start]Developed in **x86 Assembly (AT&T syntax)**, the system manages file allocation, retrieval, and optimization on a simulated storage device[cite: 117, 118]. [cite_start]It handles complex memory operations such as contiguous allocation and defragmentation, mimicking the core behavior of a file system driver[cite: 118, 128, 140].

[cite_start]The project was developed as part of the **Computer Systems Architecture (ASC)** curriculum at the **University of Bucharest**, Faculty of Mathematics and Computer Science[cite: 54, 117].

## 🛠️ Technical Features

### 1. Memory Models
The system supports two distinct memory architectures:
* [cite_start]**Linear (1D) Memory:** Simulated 8MB storage device partitioned into 1024 blocks of 8kB each[cite: 124, 125].
* [cite_start]**Bidimensional (2D) Memory:** An expanded matrix-based storage model (8MB x 8MB) where a contiguous section is considered across lines[cite: 143, 144].

### 2. Core Operations
* [cite_start]**ADD:** Allocates files contiguously based on their size in kB[cite: 128, 135]. [cite_start]It calculates the necessary number of blocks and finds the first available interval[cite: 136, 160].
* [cite_start]**GET:** Retrieves the exact block intervals (start/end) for a specific unique File ID (Descriptor)[cite: 134, 145].
* [cite_start]**DELETE:** Removes a file by its ID and frees the occupied blocks by resetting their descriptor value to 0[cite: 138, 139, 149, 150].
* [cite_start]**DEFRAGMENTATION:** A memory optimization routine that reorders stored files to eliminate gaps, moving all free space to the end of the memory while maintaining file continuity[cite: 140, 151, 311].
* [cite_start]**CONCRETE (2D only):** Interacts with the disk by scanning an absolute file path and allocating files based on their actual metadata (File ID modulo 256 and size in kB)[cite: 337, 338].

## 💻 Technical Stack
* **Language:** x86 Assembly (32-bit).
* [cite_start]**Syntax:** AT&T[cite: 114].
* **OS Environment:** Linux / Unix-based systems.
* [cite_start]**Key Concepts:** Manual memory management, hardware-level logic, CPU register optimization, and STDIN/STDOUT redirection[cite: 114, 281, 282].

## 📊 Implementation Details
* [cite_start]**File Descriptors:** Supports unique IDs between 1 and 255[cite: 131].
* [cite_start]**Storage Constraints:** Files require a minimum of 2 blocks for storage[cite: 127].
* [cite_start]**Allocation Logic:** Uses a "First Fit" approach, searching from left to right for the first available contiguous space[cite: 136, 147].

## 🚀 How to Run
To test the system using an input file (e.g., `input.txt`), use the following command:
```bash
./task_name < input.txt
