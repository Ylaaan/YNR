Allow this git : ``git config --global --add safe.directory G:/Obsidian/Documentation ``

##  Account config

```bash
git config --global user.name “[firstname lastname]”
git config --global user.email “[valid-email]”
git config --global color.ui auto
```

---

## Update & Synchronise

##### Add remote repository

```bash 
git remote add [alias] [url]
```

##### Get all branches from remote

```bash
git fetch [alias]
```

##### Merge remote and local branch

```bash
git merge [alias]/[branch]
```

##### Send local branch to remote

```bash
git push [alias] [branch]
```

##### Fetch and merge commits form remote branch (Sync from remote to local)

```bash
git pull
```

---

## Initiate

##### Create new Git repository

```bash
git init
```

##### Clone a repository

```bash
git clone [repository-url]
```

---

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

##### Commit changes

```bash
git commit -m "[message]"
```

Options : 
- Commit message : ``-m "[message]"``

---

## Branches 

##### List branches

```bash
git branch
```

##### Create new branch at commit

```bash
git branch [branch-name]
```

##### Change branch

```bash
git checkout
```

##### Merge branches

```bash
git merge [branch-name]
```

##### Show commit history

```bash
git log
```

Options :
- Follow changes across renames : ``--follow``

---

## Rewrite history

##### Apply commits form current branch ahead of specified branch

```bash
git rebase [branch-name]
```

##### Clear staging, rewrite work tree from specified commit

```bash
git reset --hard [commit]
```
