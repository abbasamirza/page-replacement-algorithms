# Page Replacement Algorithms

A comprehensive C implementation of classic operating system page replacement algorithms with an interactive command-line interface.

## Overview

This project simulates and visualizes four fundamental page replacement algorithms used in operating systems memory management. It provides an educational tool to understand how different algorithms handle page faults and memory allocation in a paging system.

## Features

- **Four Algorithm Implementations**:
  - **FIFO (First In First Out)**: Replaces the oldest page in memory
  - **OPR (Optimal Page Replacement)**: Replaces the page that won't be used for the longest time
  - **LRU (Least Recently Used)**: Replaces the page that hasn't been used for the longest time
  - **SCA (Second Chance Algorithm)**: Enhanced FIFO with a reference bit for second chances

- **Interactive Menu System**: Easy-to-navigate interface for algorithm selection
- **Visual Frame State Display**: Real-time visualization of page frames during execution
- **Performance Metrics**: Displays page hits, page faults, and hit/miss ratios
- **Flexible Input Methods**: 
  - Interactive prompts
  - Command-line arguments
- **Dynamic Configuration**: Change reference strings and frame sizes on the fly
- **Multi-threaded Execution**: Each algorithm runs in its own thread using POSIX threads

## Usage

### Building the Project

```bash
make
```

### Running the Program

**Method 1: Interactive Mode**
```bash
./main
```

**Method 2: Command-Line Arguments**
```bash
./main 1 2 3 4 5 1 2 3 4 5
```

### Menu Options

1. Run FIFO Algorithm
2. Run Optimal Page Replacement
3. Run Least Recently Used
4. Run Second Chance Algorithm
5. Run All Algorithms (compare results)
6. Change Reference String
7. Change Frame Size
8. Exit

## How It Works

### Program Flow

1. **Initialization**: User provides a reference string (sequence of page numbers) and frame size (memory capacity)
2. **Algorithm Selection**: Choose one or multiple algorithms from the interactive menu
3. **Simulation**: The selected algorithm processes each page in the reference string
4. **Visualization**: Frame states are displayed with color coding:
   - 🟢 **Green**: Page hit (page already in frame)
   - 🔵 **Blue**: Page fault with empty frame available
   - 🔴 **Red**: Page fault requiring replacement
5. **Results**: Statistics showing page hits, page faults, and percentages

### Algorithm Details

- **FIFO**: Maintains a circular queue; replaces pages in order of arrival
- **OPR**: Looks ahead in the reference string to find the optimal page to replace
- **LRU**: Tracks page access history to determine the least recently used page
- **SCA**: Uses reference bits to give pages a second chance before replacement

## File Structure

```
.
├── main.c           # Entry point and menu logic
├── algorithms.c     # Implementation of all four algorithms
├── algorithms.h     # Algorithm function declarations
├── helpers.c        # Utility functions for input, display, and frame management
├── helpers.h        # Helper function declarations and data structures
├── messages.c       # User-facing messages and menu display
├── messages.h       # Message declarations
└── makefile         # Build configuration
```

## Requirements

- GCC compiler
- POSIX-compliant system (for pthread support)
- Linux/Unix environment (uses ANSI color codes and system calls)

## Example Output

```
Incoming    Frame 1  Frame 2  Frame 3
1           1        -        -
2           1        2        -
3           1        2        3
4           4        2        3

Page Hits: 5 -> 25%
Page Faults: 15 -> 75%
```

## Educational Value

This project demonstrates:
- Memory management concepts in operating systems
- Algorithm efficiency comparison
- Thread-based concurrent execution
- Dynamic memory allocation
- Modular C programming structure

## License

Open source project for educational purposes.
