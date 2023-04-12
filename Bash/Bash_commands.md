## File manipulation

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

## Posix permissions

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

Options : /comm
- Verbose : ``-v`` or ``--verbose``
- Verbose but only when changes are applied : ``-c`` or ``--changes``
- Recursive mode : ``-R`` or ``--recursive``