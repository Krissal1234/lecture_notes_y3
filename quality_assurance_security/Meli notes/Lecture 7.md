

buffer overrun/buffer overflow attack

Buffers are memory storage regions that temporarily hold data while it is being transferred from one location to another. A buffer overflow (or buffer overrun) occurs when the volume of data exceeds the storage capacity of the memory buffer. As a result, the program attempting to write the [data to the buffer overwrites adjacent memory locations](https://www.imperva.com/learn/data-security/structured-and-unstructured-data/).


## What is a Buffer Overflow Attack

Attackers exploit buffer overflow issues by overwriting the memory of an application. This changes the execution path of the program, triggering a response that damages files or exposes private information. For example, an attacker may introduce extra code, sending new instructions to the application to gain access to IT systems.

If attackers know the memory layout of a program, they can intentionally feed input that the buffer cannot store, and overwrite areas that hold executable code, replacing it with their own code. For example, an attacker can overwrite a pointer (an object that points to another area in memory) and point it to an exploit payload, to gain control over the program.
![[Pasted image 20240521215901.png]]

1. **Buffer Overruns in C and C++**:
    
    - A critical issue where excess data overwrites memory, leading to vulnerabilities.
    - Both languages provide mechanisms that, if misused, can lead to such overruns.
2. **C++20 and `span`**:
    
    - Introduction of `span` to manage contiguous sequences safely, reducing the risk of buffer overruns.
3. **Programmer Pitfalls**:
    
    - The risk of buffer overruns is akin to "shooting oneself in the foot" due to the complexity and flexibility of C and C++.
4. **Evolution of C++**:
    
    - Continuous improvements in the C++ language to enhance safety and reduce risks associated with manual memory management.



