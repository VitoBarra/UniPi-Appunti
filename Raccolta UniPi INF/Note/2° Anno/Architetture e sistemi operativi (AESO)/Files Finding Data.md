---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Files Finding Data
---
Once a [[file system]] has translated a file name into a file number using a directory, the file
system must be able to find the blocks that belong to that file. In addition to this functional
requirement, implementations of files typically target five other goals:

- Support sequential data placement to maximize sequential file access
- Provide efficient random access to any file block
- Limit overheads to be efficient for small files
- Be scalable to support large files
- Provide a place to store per-file metadata such as the file’s reference count, owner,
access control list, size, and access time

![[Untitled 47.png]]


