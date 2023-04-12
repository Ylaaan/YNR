## Move in the file system

```bash
cd [path]
```

Path structure :
- Path of parent directory : ``../``
- Path of current directory : ``./``
- Path of home directory : ``~/``
- Path of root directory : ``/``

## File manipulation

##### List files

```bash
ls [directory-to-list]
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

##### Print file's content

```bash
cat [file-path]
```

##### Copy files

```bash
cp [source-path] [destination-path]
```

Options : 
- Copy recursively : ``-r``

##### Move files

```bash
mv [source-path] [destination-path]
```

##### Remove file

```bash
rm [file-path]
```

Options : 
- Remove even if not empty : ``-f``
- Remove even if file is a directory : ``-r``

##### Create file

```bash
touch [file-path]
```

##### Add content in file without editor

```bash
echo "[content-to-add]" [>|>>] [file]
```

Use ``>`` to replace content.
Use ``>>`` to append.

## Posix permissions

##### Execute file with root permissions

```bash
sudo [command]
```

##### Change current user

```bash
su - [user]
```

To change to root without root password : ``sudo su -``

##### Change file rights

```bash
chmod +[r;w;x] [file-path]
```

##### Change owner of file

```bash
chown [new-owner]:[new-group] [file]
```

Options : 
- Verbose : ``-v`` or ``--verbose``
- Verbose but only when changes are applied : ``-c`` or ``--changes``
- Recursive mode : ``-R`` or ``--recursive``

##### Change owner group of file

```bash
chgrp [new-group] [file]
```

Options : 
- Verbose : ``-v`` or ``--verbose``
- Verbose but only when changes are applied : ``-c`` or ``--changes``
- Recursive mode : ``-R`` or ``--recursive``

## System Checks

##### Check running processes

```bash
ps [option]
```

Options :
- List all processes : ``-A``
- Only running : ``-r``
- All processes on this terminal : ``-T``

##### Check file system

```bash
df [options]
```

Options : 
- Human readable : ``-h``
- Show all : ``-a`` or ``--all``
- Show only local : ``-l`` or ``--local``