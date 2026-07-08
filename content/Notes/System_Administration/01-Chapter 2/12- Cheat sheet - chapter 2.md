---
title: Chapter 1 cheatsheet 
date:  2026-07-06T12:21:10+05:30
params:
    author: 0x-s0M3n4th
draft: false
weight: 12 
tags: ["Linux", "Basics", "cheatsheet"]
---


## Main commands:

| Commands | Short description |
| -------- | ----------------- |
|  ls -l   |  Lists files in a long format showing permissions, owner, and size.                |
|  ls -a   |  Lists all files, including hidden ones (those starting with a dot).                 |
|  ls -ld  |  Lists details of the directory itself rather than its contents.                 |
|  ls -lh  |  Lists files in long format with file sizes in human-readable format (KB, MB).                 |
|  ls -lt  |  Lists files sorted by modification time, newest first.                 |
|  ls -ltr |  Lists files sorted by modification time in reverse order (oldest first).                 |
|  ls -R   |  Lists all files in the current directory and all subdirectories recursively.                 |
|  pwd     |  Prints the full path of the current working directory.                 |
|  cd ..   |  Moves one level up into the parent directory                 |
|  cd `dir_name` | Changes the current directory to the specified folder             |
|  cd ~    |  Moves directly to the current user's home directory.                 |
|  cd -    |  Switches back to the previous directory you were in.                 |
|  cd      |  Shortcut to return to the home directory.                 |
|  tree -a |  Displays all files and directories in a tree structure, including hidden ones.                 |
|  tree -d |  Displays only directories in the tree structure.                 |
|  tree -h |  Displays the tree structure along with human-readable file sizes.                 |
|  tree -f |  Displays the full path prefix for each file in the tree.                 |
|  tree -p |  Displays the tree structure along with file permissions.                 |
|  tty     |  Prints the file name of the terminal connected to standard input.                 |
|  uptime  |  Shows how long the system has been running and the current load.                 |
|  clear   |  Clears the terminal screen for a fresh workspace.                 |
|  which `command_name` | Shows the full path of the executable for a command.      |
|  whereis `command_name` | Locates the binary, source, and manual page files for a command.    |
|  type `command_name` | Explains how a command name would be interpreted (alias, builtin, or file).       |
|  uname   |  Prints the name of the operating system kernel.                 |
|  uname -a | Prints all available system information in one line.                 |
|  uname -s | Displays the kernel name.                 |
|  uname -n | Displays the network node hostname.                 |
|  uname -r | Displays the kernel release version.                 |
|  uname -v | Displays the kernel version date and build info.                 |
|  uname -m | Displays the machine hardware architecture (e.g., x86_64).                 |
|  uname -p | Displays the processor type or "unknown".                 |
|  uname -i | Displays the hardware platform or "unknown".                 |
|  uname -o | Displays the operating system name (e.g., GNU/Linux).                 |
|  lscpu   |  Displays detailed information about the CPU architecture.                 |
|  man `cmd_name` | Opens the official manual page for a specific command.            |
|  man -k `cmd_name` |  Searches the manual descriptions for a specific keyword.        |
|  appropos `cmd_name` | Searches the manual pages for a keyword (same as man -k).       |
|  `cmd_name --help` |  Displays a brief summary of a command's options and usage.         |
|  `cmd_name` -? | An alternative flag used by some programs to show help.             |
|  ls -l /usr/share/doc/`cmd_name`          |  Checks for additional offline documentation files for a program.             |

