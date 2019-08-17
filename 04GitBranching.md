# Git Branch

solution of [learngitbranching](https://learngitbranching.js.org/)

## Section1-git local

```bash
# 1.1 commit: A commit in a git repository records a snapshot of all the files in your directory
git commit
git commit

# 1.2 branches: They are simply pointers to a specific commit
git checkout -b bugFix

# # or
# git branch bugFix
# git checkout bugFix

# 1.3 merge
git checkout -b bugFix
git commit
git checkout master
git commit
git merge bugFix

# # 1.4 Rebase
# git checkout -b bugFix
# git commit
# git checkout master
# git commit
# git checkout bugFix
# git rebase master # HEAD is on bugFix

git checkout -b bugFix
git commit
git checkout master
git commit
git rebase master bugFix # HEAD is on bugFix

# 2.1 Detached HEAD: from HEAD>master>C4 to HEAD>C4
git checkout C4
# 2.2 
git checkout C4^

# 2.3 switch branch
git branch -f master C6
git branch -f bugFix C0
git checkout C1

# # 2.4 reset, revert
# git reset C1
# git checkout pushed
# git revert C2

git reset local~
git checkout pushed
git revert pushed # or git revert HEAD

# 3.1 cherry-pick
git cherry-pick C3 C4 C7

# 3.2 Rebase interactive
git rebase -i C1 
# or git rebase -i overHere
# or git rebase -i master~4

# 4.1 Grabbing Just 1 Commit
git checkout master
git cherry-pick C4

# 4.2 Juggling Commits 1
git rebase -i master
git commit --amend
git rebase -i master
git branch -f master caption # git rebase caption master

# 4.3 Juggling Commits 2
# git cherry-pick will plop down a commit from anywhere in the tree onto HEAD (as long as that commit isn't an ancestor of HEAD).
git checkout master
git cherry-pick C2
git commit --amend
git cherry-pick C3

# 4.4 Tag: you can then reference tags like a branch.
git tag v0 C1
git tag v1 C2
git checkout C2

# 4.5 describe: describe where you are relative to the closest tag.
# git describe master
# git describe side
git commit

# 5.1 Rebase multiple branches
git rebase master bugFix
git rebase bugFix side
git rebase side another
git rebase another master # git branch -f master another

# 5.2 Multiple parents
git branch bugWork master~^2~

# 5.3 Branch Spaghetti
git checkout one
git cherry-pick C4 C3 C2
git checkout two
git cherry-pick C5 C4 C3 C2
git branch -f three C2

git rebase master one
git rebase -i C1
git rebase master two
git rebase -i C1
git rebase C2  three
```

## Section2-git remote

```bash
# 1.1 clone intro
git clone

# 1.2 origin/master checkout
git commit
git checkout o/master
git commit

# 1.3 git fetch
git fetch

# 1.4 git pull details
git fetch
git merge o/master
# above 2 commands are equal to `git pull`

# 1.5 Fake Teamwork
git clone
git fakeTeamwork 2
git commit
git pull

# 1.6 git push
git clone
git commit
git commit
git push

# 1.7 Diverged History
git clone
git fakeTeamwork
git commit
git pull --rebase
git push

# 2.1 pull --rebase
git rebase -i master side1
git rebase side1 side2
git rebase side2 side3
git rebase side3 master
git pull --rebase
git push

# or
git fetch
git rebase o/master side1
git rebase side1 side2
git rebase side2 side3
git rebase side3 master
git push

# 2.2 pull by merge
git rebase side1 master
git pull
git merge side2
git merge side3
git push

# 2.3 tracking remote
git checkout -b side o/master # git branch -u o/master side
git commit
git pull --rebase
git push

# 2.4 remote push
git push origin master
git push origin foo

# 2.5 push args
git push origin foo:master
git push origin master^:foo

# 2.6 fetch args, <source>:<destination>
git fetch origin foo:master
git fetch origin master^:foo
git checkout foo
git merge master

# 2.7 delete remote
git push origin :foo
git pull origin :bar

# 2.8 pull args
git pull origin bar:foo
git pull origin master:side
````