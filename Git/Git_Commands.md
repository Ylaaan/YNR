##  Account config

```bash
git config --global user.name “[firstname lastname]”
git config --global user.email “[valid-email]”
git config --global color.ui auto
```

## Initiate

##### Create new Git repository

```bash
git init
```

##### Clone a repository

```
git clone [repository-url]
```

## Staging

##### Show status

```bash
git status
```

##### Add files to stage

```bash
git add [files]
```

For all files : ``*``

##### Unstage file (doesn't cancel changes)

```bash
git reset
```

##### Get changes

```bash
git diff
```

Options : 
- Show non commited changes : ``--staged``

##### Commit

```bash
git commit -m "[message]"
```

Options : 
- Commit message : ``-m "[message]"``

/com