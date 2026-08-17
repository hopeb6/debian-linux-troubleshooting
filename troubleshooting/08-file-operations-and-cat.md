# 08 — Linux File Operations and the `cat` Command

## Environment

- OS: Debian GNU/Linux 13 (Trixie)
- Desktop: KDE Plasma 6
- Shell: Bash

## Problem

While practising Linux file commands, I wanted to combine the contents of two XML files and save the result in the `Documents` directory.

An initial attempt failed because the files were not in the current directory and the output path was interpreted relative to the current directory.

## Investigation

### Command

```bash
pwd
```

### Why

`pwd` shows the current working directory. This is important because relative paths are interpreted from the directory shown by `pwd`.

### Command

```bash
ls
```

### Why

`ls` shows the files and directories in the current directory.

### Command

```bash
find ~ -name "*.xml"
```

### Why

This searches the home directory for XML files and helps establish their actual paths.

## Understanding `cat`

### Command

```bash
cat file.txt
```

### Why

`cat` reads a file and writes its contents to standard output.

Multiple files can be supplied:

```bash
cat file1.txt file2.txt
```

Their contents are output sequentially.

### Redirection

```bash
cat file1.txt file2.txt > combined.txt
```

The `>` operator redirects the output into a new file called `combined.txt`.

This combines the **contents** of the two files; it does not move the two files themselves.

## Why the earlier command failed

The XML files were located in `Downloads`, while the command was being executed from another directory.

A relative filename such as:

```text
file.xml
```

means "look in the current directory."

A relative path such as:

```text
Downloads/file.xml
```

means "look in the Downloads directory relative to the current directory."

An absolute path such as:

```text
/home/suby/Downloads/file.xml
```

identifies the file regardless of the current directory.

## `cat` vs `cp` vs `mv`

### Read or combine contents

```bash
cat file1 file2 > combined.txt
```

### Copy the files

```bash
cp file1 file2 Documents/
```

### Move the files

```bash
mv file1 file2 Documents/
```

These commands perform different operations and should not be treated as interchangeable.

## Result

A combined output file could be created in `Documents` from the `Downloads` directory using a path such as:

```bash
cat file1.xml file2.xml > ../Documents/odoo.txt
```

This was a useful practical exercise in:

- current working directories
- relative paths
- output redirection
- file contents
- `cat`
- `cp`
- `mv`

## Important Note

Concatenating two XML documents literally does **not** necessarily produce a valid XML or MS Project document. `cat` operates on text; it does not understand XML structure.

## Lesson Learned

Linux commands can operate on files outside the current directory as long as the correct relative or absolute path is supplied.

The main distinction is:

- `cat` → read/concatenate **contents**
- `cp` → copy **files**
- `mv` → move/rename **files**
- `cd` → change **directory**
- `pwd` → show **current directory**
- `ls` → list **directory contents**

## Skills Demonstrated

- Bash
- Linux filesystem navigation
- Relative and absolute paths
- Output redirection
- File operations
- Command-line troubleshooting
