# Bash Commands

## Table of contents

- [Bash Commands](#bash-commands)
  - [Table of contents](#table-of-contents)
  - [📂Move in the file system📂](#move-in-the-file-system)
    - [Show current directory](#show-current-directory)
    - [Move to path](#move-to-path)
    - [Locate binary, source, manual-page files of a command](#locate-binary-source-manual-page-files-of-a-command)
    - [Check current user](#check-current-user)
    - [Change current user](#change-current-user)
    - [Exit user or command line](#exit-user-or-command-line)
  - [📝File manipulation📝](#file-manipulation)
    - [List files](#list-files)
    - [Print file's content](#print-files-content)
    - [Copy files](#copy-files)
    - [Move files](#move-files)
    - [Remove file](#remove-file)
    - [Create file](#create-file)
    - [Add content in file without editor](#add-content-in-file-without-editor)
  - [✔️POSIX permissions❌](#️posix-permissions)
    - [Execute file with root permissions](#execute-file-with-root-permissions)
    - [Change file rights](#change-file-rights)
    - [Change owner of file](#change-owner-of-file)
    - [Change owner group of file](#change-owner-group-of-file)
  - [📊System Checks📊](#system-checks)
    - [Check running processes](#check-running-processes)
    - [Check file system](#check-file-system)
    - [Check file size](#check-file-size)
  - [⛰️Environement variables🏞️](#️environement-variables️)
    - [List environement variables](#list-environement-variables)
    - [Set environement variable](#set-environement-variable)
  - [💻 .bashrc 💻](#-bashrc-)
    - [Fix watch command for aliases](#fix-watch-command-for-aliases)
    - [Apply Modifications of .bashrc file](#apply-modifications-of-bashrc-file)
    - [Functions](#functions)

## 📂Move in the file system📂

### Show current directory

```bash
pwd
```

### Move to path

```bash
cd <path>
```

Path structure :

- Path of parent directory : ``../``
- Path of current directory : ``./``
- Path of home directory : ``~/``
- Path of root directory : ``/``

### Locate binary, source, manual-page files of a command

```bash
whereis <name>
```

Options :

- Search for binarires only : ``-b``
- Search manuals and info  only : ``-m``
- Search for sources only : ``-s``

### Check current user

```bash
whoami
```

### Change current user

```bash
su - <user>
```

To change to root without root password : ``sudo su -``

### Exit user or command line

```bash
exit
```

## 📝File manipulation📝

### List files

```bash
ls <directory-to-list>
```

Options :

- Also list hidden files : ``-a`` or ``--all``
- List files permissions : ``-l``
- Human-readable mode : ``-h``
- List with colors : ``-C``
- Only list directories : ``-d`` or ``--directory``
- Show inodes : ``-i``
- Recursive mode : ``-R`` or ``--recursive``
- One file per line : ``-1``

### Print file's content

```bash
cat <file-path>
```

### Copy files

```bash
cp <source-path> <destination-path>
```

Options :

- Copy recursively : ``-r``

### Move files

```bash
mv <source-path> <destination-path>
```

### Remove file

```bash
rm <file-path>
```

Options :

- Remove even if not empty : ``-f``
- Remove even if file is a directory : ``-r``

### Create file

```bash
touch <file-path>
```

### Add content in file without editor

```bash
echo "<content-to-add>" >|>> <file>
```

Use ``>`` to replace content.
Use ``>>`` to append.

## ✔️POSIX permissions❌

### Execute file with root permissions

```bash
sudo <command>
```

### Change file rights

```bash
chmod +<r;w;x> <file-path>
```

### Change owner of file

```bash
chown <new-owner>:<new-group> <file>
```

Options :

- Verbose : ``-v`` or ``--verbose``
- Verbose but only when changes are applied : ``-c`` or ``--changes``
- Recursive mode : ``-R`` or ``--recursive``

### Change owner group of file

```bash
chgrp <new-group> <file>
```

Options :

- Verbose : ``-v`` or ``--verbose``
- Verbose but only when changes are applied : ``-c`` or ``--changes``
- Recursive mode : ``-R`` or ``--recursive``

## 📊System Checks📊

### Check running processes

```bash
ps <options>
```

Options :

- List all processes : ``-A``
- Only running : ``-r``
- All processes on this terminal : ``-T``

### Check file system

```bash
df <options>
```

Options :

- Human readable : ``-h``
- Show all : ``-a`` or ``--all``
- Show only local : ``-l`` or ``--local``

### Check file size

```bash
du <options> <./*>
```

Options :

- Summarize : ``-s``
- Human-readable mode : ``-h``

## ⛰️Environement variables🏞️

### List environement variables

```bash
env
```

### Set environement variable

```bash
export <name>=<value>
```

Options :

- Show exported variables : ``-p``

## 💻 .bashrc 💻

### Fix watch command for aliases

Add the folowing line to your .bashrc file.

```bash
alias watch="watch ";
```

### Apply Modifications of .bashrc file

```bash
source ~/.bashrc
```

### Functions

For more complicated case using a function might be better

```bash
function <name_of_the_function>() {
    <commands>
}
```

You can use ``$@`` to get all parameters at once
