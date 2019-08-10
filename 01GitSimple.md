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
