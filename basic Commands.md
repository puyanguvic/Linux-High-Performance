# `cat` Command in Linux

The `cat` command in Linux/Unix systems is used to display, concatenate, or create file content. The name comes from "concatenate." It is often used to read files and output their content, and it can also be used to create or merge files.

## Basic Usage

### 1. Displaying File Content
You can use the `cat` command to display the content of a file:
```bash
cat filename
```
Example:
```bash
cat file.txt
```
This will display the content of `file.txt`.

### 2. Merging Multiple Files
You can use `cat` to concatenate and output the content of multiple files:
```bash
cat file1.txt file2.txt
```
This will display the contents of both `file1.txt` and `file2.txt` in sequence.

### 3. Redirecting Output to a File
Using the `>` or `>>` redirection symbols, you can write the output of `cat` into a file:
- `>` will overwrite the target file:
    ```bash
    cat file1.txt > newfile.txt
    ```
    This writes the content of `file1.txt` to `newfile.txt`, overwriting it if it already exists.

- `>>` will append the content to the target file:
    ```bash
    cat file2.txt >> newfile.txt
    ```
    This appends the content of `file2.txt` to the end of `newfile.txt`.

### 4. Creating a File
You can create a new file and write content to it using `cat`:
```bash
cat > newfile.txt
```
After entering the content, press `Ctrl + D` to save and exit. This creates `newfile.txt` and writes the content to it.

### 5. Displaying Line Numbers with Content
To display file content with line numbers, use the `-n` option:
```bash
cat -n filename
```
Example:
```bash
cat -n file.txt
```
Output:
```
     1  First line
     2  Second line
     3  Third line
```

### 6. Showing Non-printing Characters
Use the `-A` or `-vET` option to display special characters, such as tabs and end-of-line symbols:
```bash
cat -A filename
```
Example:
```bash
cat -A file.txt
```
This will show the end-of-line symbol as `$` and tabs as `^I`.

## Common Options Summary
- `-n`: Display line numbers.
- `-b`: Like `-n`, but doesn't number blank lines.
- `-A`: Show all non-printing characters, including newlines and tabs (equivalent to `-vET`).
- `-E`: Show `$` at the end of each line.
- `-T`: Show tabs as `^I`.
- `-s`: Compress consecutive blank lines into a single line.

## Examples

### 1. Merge Two Files and Output to a Third File
```bash
cat file1.txt file2.txt > merged.txt
```

### 2. Display File Content with Line Numbers
```bash
cat -n file.txt
```

### 3. Create and Write to a File
```bash
cat > newfile.txt
```
After entering the content, press `Ctrl + D` to save.

The `cat` command helps with viewing, merging, and creating files, making it an essential tool for managing files in everyday Linux usage.
