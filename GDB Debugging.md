# Introduction to GDB
GDB is the GNU Project's debugger, allowing you to see what is going on inside a program while it executes or what a program was doing at the moment it crashed. It supports debugging programs written in C, C++, and other languages.

## Why Use GDB?
- Identify and Fix Bugs: Step through code to find logical errors.
- Inspect Program state: Examine variables, memory, and the call stack.
- Control Execution: Pause execution at specific points to investigate issues.
- Improve Understanding: Learn how code behaves during runtime.

# Setting Up the Environment
## Installing GDB
On Linux: GDB is usually pre-installed. If not, install it using your package manager (e.g., ``` sudo apt-get install gdb```).

## Compiling Programs for Debugging
Ensure that you compile your programs with debugging symbols to get the most out of GDB.
```
gcc -g -o program program.c
```
- The ``` -g ``` flag includes debugging information
- Avoid optimization flags (like ``` -02 ```) during debugging, as they can rearrange code execution.

# Basic GDB Commands
- Start GDB with a Program:
```
gdb ./program
```
- Exit GDB:
```
(gdb) quit
```

- Running Programs
  - Run the Program:
  ```
  (gdb) run
  ```
  - Run with Arguments:
  ```
  (gdb) run arg1 arg2
  ```
- Breakpoints
  - Set a Breakpoint at a function:
  ```
  (gdb) break function_name
  ```
  - Set a Breakpoint at a Line Number:
  ```
  (gdb) break filename.c:line_number
  ```
  - List Breakpoints
  ```
  (gdb) info breakpoints
  ```
  - Delete a Breakpoints
  ```
  (gdb) delete breakpoint_number
  ```

- Stepping Through Code
  - Continue Execution:
  ```
  (gdb) continue
  ```
  - Step into Functions:
  ```
  (gdb) step
  ```
  - Step Over Functions:
  ```
  (gdb) next
  ```
  - Finish Current Function:
  ```
  (gdb) finish
  ```

- Inspecting Variables
  - Print Variable Value:
    ```
    (gdb) print variable_name
    ```
  - Print All local Variables:
    ```
    (gdb) info locals
    ```
  - Display Variable Every Time Execution Stops:
    ```
    (gdb) display variable_name
    ```

- Backtraces
  - View Call Stack
  ```
  (gdb) backtrace
  ```
  - Move Up and Down the Stack:
  ```
  (gdb) up
  (gdb) down
  ```

# Advanced GDB Features
## Conditional Breakpoints
- Set Breakpoint with Condition:
```
(gdb) break function name if (condition)
```

## Watchpoints
- Set a Watchpoint on a Variable:
```
(gdb) watch variable_name
```
- Set a Read Watchpoint:
```
(gdb) rwatch variable_name
```

## Inspecting Memory
- Examine Memory at Address:
```
(gdb) x /format address
```
  - Formats:
    - ``` x ``` - Hexadecimal
    - ``` d ``` - Decimal
    - ``` c ``` - Character
    - ``` s ``` - String
    - Exampe: ``` (gdb) x /4xw 0x7fffffffe000 ```
     
## Modifying Variables at Runtime
- Set Variable Value:
```
(gdb) set variable_name = new_value
```
## Scripting and Automation
- GDB Scripts:
  - Create a file (e.g., ``` gdb_commands.gdb) with GDB commands
  - Run GDB with the script:
  ```
  gdb -x gdb_commands.gdb ./program
  ```
# Practical Debugging Scenarios
## Debugging Segmentation Faults
- Run the Program:
```
(gdb) run
```
- When it Crashes, View the backtrace:
```
(gdb) backtrace
```
- Inspect Variables and Memory:
```
(gdb) print variable_name
```
- Check Points and Array Indexs
## Memory Leaks and Corruption
- Use tools like **Valgrind** alongside GDB to detect memory issues.
- **Insepct Dynamic Memory Allocation**
  - Check for proper use of ```malloc```, ```calloc```, ```realloc```, and ```free```.
## Logical Errors
- Set Breakpoints at Key Functions.
- Step Through Code to Observe Logic Flow.
- Inspect Variable Values at Each Step.

## Multithreaded Debugging
- List Threads:
```
(gdb) info threads
```
- Switch Between Threads.
```
(gdb) thread thread_number
```
Set Breakpoints in Specific Threads.
```
(gdb) break function_name thread thread_number
```

# Interview Tips and Strategies
## Common Interview Questions
- Explain How You Debug a Segmentation Fault.
- Describe How to Use Breakpoints and Watchpoints.
- Demonstrate Finding a Memory Lack
- Debug a Provided Code Snippet Live

## Demonstrating Problem-Solving Skills
- Think Aloud: Explain your thought process.
- Be Methodical: Start from known points and procceed step by step
- Use GDB Efficiently: Show familiarity with commands.

## Communicating Effectively
- Clarify Questions: Ensure you understand the problem.
- Explain Actions: Describe what you're doing and why.
- Ask for Input: If unsure, ask the interviewer for clarification.

# Additional Resources
## Recommended Books
- **"The Art of Debugging with GDB, DDD, and Eclipse"** by Nome Matloff and Peter Jay Salzman
- **"GDB Pocket Reference"** by Arnold Robbins.
## Online Tutorials and Documentation
- **GDB official Documentation:**
  https://www.gnu.org/software/gdb/documentation/
- **GDB User Manual:** Comprehensive guide covering all aspects of GDB.

## Practice Exercises
- Debugging Practice:
  - Write a small program with intentional bugs to practice.
  - Use open-source projects to explore real-world debugging.
- Online Platforms:
  - **LeetCode** and **HackerRank** sometimes include debugging challenges.
  - Debugging challenges on educational platform
