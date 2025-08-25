# Sudoku Board Validator

A C program that validates the state of a Sudoku puzzle board by checking if all rows and columns contain valid values according to Sudoku rules.

## Overview

This program reads a Sudoku board from a text file and verifies whether the board is in a valid state. It checks that each row and column contains only valid digits (1 to board size) or blanks (represented by 0), with no duplicate digits in any row or column.

## Features

- Reads Sudoku board data from text files
- Dynamically allocates memory for boards of any size
- Validates both rows and columns for:
  - Proper value ranges (0 to board size)
  - No duplicate digits within rows
  - No duplicate digits within columns
- Returns "valid" or "invalid" based on board state
- Proper memory management with complete cleanup

## File Format

Input files must follow this format:
- First line: Single integer representing board size (N for N×N board)
- Subsequent N lines: Comma-separated values representing board rows
- Values can be 0 (blank) or digits 1 to N

Example (3×3 board):
```
3
1,2,3
0,0,0
3,2,1
```

## Usage

```bash
./check_board <filename>
```

### Arguments
- `filename`: Path to the Sudoku board file to validate

### Output
- Prints "valid" if the board state is valid
- Prints "invalid" if the board state violates Sudoku rules
- Exits with error code 1 if file cannot be read or parsed

## Building

Compile the program with:
```bash
gcc -o check_board check_board.c
```

## Examples

```bash
# Valid board
./check_board board3.txt
valid

# Invalid board (duplicates in row/column)
./check_board invalid_board.txt
invalid

# File error
./check_board nonexistent.txt
Can't open file for reading.
```

## Error Handling

The program handles various error conditions:
- Incorrect number of command line arguments
- File opening failures
- Memory allocation failures
- File reading errors
- Invalid board size values

## Implementation Details

- Uses dynamic memory allocation for 2D arrays
- Implements proper pointer arithmetic for array access
- Includes comprehensive memory cleanup
- Uses `getline()` for safe file reading
- Implements tokenization for parsing CSV data
