# Hash Table Dictionary for Spell Checker

This project implements a dictionary using a hash table in C. It is designed to efficiently check the spelling of words by loading a dictionary file into memory, allowing for fast lookups, and supporting dynamic memory management for loading and unloading the dictionary.

## Features

- **Hash Table Implementation:**  
  Uses a hash table with separate chaining (linked lists) to handle collisions. The number of buckets (`N`) is set to 10,000 for efficient distribution.

- **Efficient Word Lookup:**  
  Provides a `check` function to determine if a word exists in the loaded dictionary, using case-insensitive comparison.

- **Dictionary Loading:**  
  Reads words from a dictionary file, hashes each word, and inserts it into the appropriate bucket in the hash table.

- **Memory Management:**  
  Dynamically allocates memory for each word node and provides an `unload` function to free all allocated memory when done.

- **Word Counting:**  
  Tracks and returns the number of words loaded into the dictionary.

## How It Works

- **Data Structure:**  
  Each bucket in the hash table is a pointer to a linked list of nodes. Each node contains a word and a pointer to the next node.

- **Hash Function:**  
  Uses the djb2 hash function (by Dan Bernstein) to hash words to a bucket index.

- **Loading:**  
  The `load` function reads each word from the dictionary file, creates a new node, and inserts it at the beginning of the linked list for the appropriate bucket.

- **Checking:**  
  The `check` function hashes the input word and traverses the linked list at the corresponding bucket, comparing each word case-insensitively.

- **Unloading:**  
  The `unload` function iterates through each bucket and frees all nodes in the linked lists.

## File Structure

- `dictionary.c` — Contains all logic for the hash table dictionary (loading, checking, unloading, and size).
- `dictionary.h` — Header file with function prototypes and type definitions (not shown here).

## Example Usage

This code is typically used as part of a larger spell checker program. Example workflow:

1. Load a dictionary file:
    ```c
    load("dictionary.txt");
    ```
2. Check if a word exists:
    ```c
    if (check("example")) { /* ... */ }
    ```
3. Get the number of words loaded:
    ```c
    unsigned int n = size();
    ```
4. Unload the dictionary and free memory:
    ```c
    unload();
    ```

## Notes

- The hash table size (`N`) can be adjusted for different dictionary sizes and performance needs.
- The implementation assumes the dictionary file contains one word per line.
- All memory allocated for nodes is properly freed by the `unload` function.

---

This project demonstrates the use of hash tables, linked lists, and dynamic memory management in C for efficient word lookup and dictionary
