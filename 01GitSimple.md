# Git Simple Operation

## Introduction

**Test Installation**

`git --version`

**Minimal Config**

```bash
# Set name, email
git config --global user.name "Your Name" # "Your Name"可以与github用户名不同
git config --global user.email "email@example.com"

# find name, email
git config --list
```

local, global, system:

```bash
git config --local # only for a repo
git config --global # for all repos of current user(recommended)
git config --system # 对系统所有登录的用户有效
```

```bash
# list config
git config --list --local
git config --list --global
git config --list --system

# all config
git config --list
```

## Git New

Empty Directory: 

```bash
git init project_name
cd project_name
```

Not Empty Directory:

```bash
cd project_name
git init
```

## Git flow

![](Res01/git_state.png)

```bash
# check status
git status

# 1.new file

# 2. add to staged
git add file1.txt
git add dir1
git add *
git add -u # add modified file

# 3. commit
git commit -m "add file1"

# 4. push
git push origin master
```

Rename Trick:

```bash
# without trick
mv filename1 filename2
git status
git rm filename1
git add filename2
git status

# disgard all changes in staged area
git reset --hard

# rename trick
git mv filename1 filename2
```