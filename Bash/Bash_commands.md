# Bash Commands

- [📂Move in the file system📂](#%F0%9F%93%82Move%20in%20the%20file%20system%F0%9F%93%82)
	- [Show current directory](#Show%20current%20directory)
	- [Move to path](#Move%20to%20path)
	- [Locate binary, source, manual-page files of a command](#Locate%20binary,%20source,%20manual-page%20files%20of%20a%20command)
	- [Check current user](#Check%20current%20user)
	- [Change current user](#Change%20current%20user)
	- [Exit user or command line](#Exit%20user%20or%20command%20line)
- [📝File manipulation📝](#%F0%9F%93%9DFile%20manipulation%F0%9F%93%9D)
	- [List files](#List%20files)
	- [Print file's content](#Print%20file's%20content)
	- [Copy files](#Copy%20files)
	- [Move files](#Move%20files)
	- [Remove file](#Remove%20file)
	- [Create file](#Create%20file)
	- [Add content in file without editor](#Add%20content%20in%20file%20without%20editor)
- [✔️POSIX permissions❌](#%E2%9C%94%EF%B8%8FPOSIX%20permissions%E2%9D%8C)
	- [Execute file with root permissions](#Execute%20file%20with%20root%20permissions)
	- [Change file rights](#Change%20file%20rights)
	- [Change owner of file](#Change%20owner%20of%20file)
	- [Change owner group of file](#Change%20owner%20group%20of%20file)
	- [Get file name from bath](#Get%20file%20name%20from%20bath)
- [📊System Checks📊](#%F0%9F%93%8ASystem%20Checks%F0%9F%93%8A)
	- [Check running processes](#Check%20running%20processes)
	- [Check file system](#Check%20file%20system)
	- [Check file size](#Check%20file%20size)
- [⛰️Environment variables🏞️](#%E2%9B%B0%EF%B8%8FEnvironment%20variables%F0%9F%8F%9E%EF%B8%8F)
	- [List environment variables](#List%20environment%20variables)
	- [Set environment variable](#Set%20environment%20variable)
- [💻 .bashrc 💻](#%F0%9F%92%BB%20.bashrc%20%F0%9F%92%BB)
	- [Fix watch command for aliases](#Fix%20watch%20command%20for%20aliases)
	- [Apply Modifications of .bashrc file](#Apply%20Modifications%20of%20.bashrc%20file)
	- [Functions](#Functions)


## 📂Move in the file system📂

### Show current directory

```bash
pwd
```

### Move to path

```bash
cd <path>
```

Path structure:

- Path of parent directory: ``../``
- Path of current directory: ``./``
- Path of home directory: ``~/``
- Path of root directory: ``/``

### Locate binary, source, manual-page files of a command

```bash
whereis <name>
```

Options :

- Search for binaries only: ``-b``
- Search manuals and info  only: ``-m``
- Search for sources only: ``-s``

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

- Also list hidden files: ``-a`` or ``--all``
- List files permissions: ``-l``
- Human-readable mode: ``-h``
- List with colors: ``-C``
- Only list directories: ``-d`` or ``--directory``
- Show inodes: ``-i``
- Recursive mode: ``-R`` or ``--recursive``
- One file per line: ``-1``

### Print file's content

```bash
cat <file-path>
```

### Copy files

```bash
cp <source-path> <destination-path>
```

Options:

- Copy recursively: ``-r``

### Move files

```bash
mv <source-path> <destination-path>
```

### Remove file

```bash
rm <file-path>
```

Options :

- Remove even if not empty: ``-f``
- Remove even if file is a directory: ``-r``

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

### Get file name from bath

```bash
basename <path> <suffix>
```

Options: 

- You can specify a suffix (file extension) to exclude it from the output the option does the same thing `-s`
- Multiple paths at once: `-a`

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

Options:

- Verbose: ``-v`` or ``--verbose``
- Verbose but only when changes are applied: ``-c`` or ``--changes``
- Recursive mode: ``-R`` or ``--recursive``

### Change owner group of file

```bash
chgrp <new-group> <file>
```

Options:

- Verbose: ``-v`` or ``--verbose``
- Verbose but only when changes are applied: ``-c`` or ``--changes``
- Recursive mode: ``-R`` or ``--recursive``

## 📊System Checks📊

### Check running processes

```bash
ps <options>
```

Options :

- List all processes: ``-A``
- Only running: ``-r``
- All processes on this terminal: ``-T``

### Check file system

```bash
df <options>
```

Options :

- Human readable: ``-h``
- Show all: ``-a`` or ``--all``
- Show only local: ``-l`` or ``--local``

### Check file size

```bash
du <options> <./*>
```

Options:

- Summarize: ``-s``
- Human-readable mode: ``-h``

## ⛰️Environment variables🏞️

### List environment variables

```bash
env
```

### Set environment variable

```bash
export <name>=<value>
```

Options:

- Show exported variables: ``-p``

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
