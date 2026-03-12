# Minimal OS Storage Management System (x86 Assembly)

## 📌 Project Overview
This project is a low-level implementation of a **storage management component** for a minimal operating system. Developed in **x86 Assembly (AT&T syntax)**, the system manages file allocation, retrieval, and optimization on a simulated storage device. It handles complex memory operations such as contiguous allocation and defragmentation, mimicking the core behavior of a file system driver.

The project was developed as part of the **Computer Systems Architecture (ASC)** curriculum at the **University of Bucharest**, Faculty of Mathematics and Computer Science.

## 🛠️ Technical Features

### 1. Memory Models
* **Linear (1D) Memory:** Simulated 8MB storage device partitioned into 1024 blocks of 8kB each.
* **Bidimensional (2D) Memory:** An expanded matrix-based storage model (8MB x 8MB) where a contiguous section is considered across lines.

### 2. Core Operations
* **ADD:** Allocates files contiguously based on their size in kB. It calculates the necessary number of blocks and finds the first available interval.
* **GET:** Retrieves the exact block intervals (start/end) for a specific unique File ID (Descriptor).
* **DELETE:** Removes a file by its ID and frees the occupied blocks by resetting their descriptor value to 0.
* **DEFRAGMENTATION:** A memory optimization routine that reorders stored files to eliminate gaps, moving all free space to the end of the memory while maintaining file continuity.
* **CONCRETE (2D only):** Interacts with the disk by scanning an absolute file path and allocating files based on their actual metadata (File ID modulo 256 and size in kB).

## 💻 Technical Stack
* **Language:** x86 Assembly (32-bit).
* **Syntax:** AT&T.
* **OS Environment:** Linux / Unix-based systems.
* **Key Concepts:** Manual memory management, hardware-level logic, CPU register optimization, and STDIN/STDOUT redirection.

## 📊 Implementation Details
* **File Descriptors:** Supports unique IDs between 1 and 255.
* **Storage Constraints:** Files require a minimum of 2 blocks for storage.
* **Allocation Logic:** Uses a "First Fit" approach, searching from left to right for the first available contiguous space.

## 🚀 How to Run
To test the system using an input file (e.g., `input.txt`), use the following command:
```bash
./task_name < input.txt
