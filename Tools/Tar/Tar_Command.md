# Tar Command

- [Command syntax](#Command%20syntax)
- [Basic usage](#Basic%20usage)
	- [Create an archive file from the file README.txt and directory src](#Create%20an%20archive%20file%20from%20the%20file%20README.txt%20and%20directory%20src)
	- [Extract contents for the into the current directory](#Extract%20contents%20for%20the%20into%20the%20current%20directory)
	- [Extract contents for.tar.gz into the current directory](#Extract%20contents%20for.tar.gz%20into%20the%20current%20directory)


## 📖Command syntax📖

```bash
tar <options> <name_of_the_tar_archive> <files_to_include>
```

Options:

- Create a new archive: ``-c``, ``--create``
- Append files to the end of an archive:  ``-r``, ``--append``
- Extract files from an archive: ``-x``, ``--extract``, ``--get``
- Specify the archive's name: ``-f``, ``--file``
- show a list of files and folders in the archive: ``-t``, ``--list``
- Show a list of processed files: ``-v``, ``--verbose``

## 🔧Basic usage🔧

### Create an archive file from the file README.txt and directory src

```bash
tar -cvf <archive_name>.tar README.txt <src>
```

### Extract contents for the into the current directory

```bash
tar -xvf <archive_name>
```

### Extract contents for.tar.gz into the current directory

```bash
tar -xvf <archive_name>.gz
```
