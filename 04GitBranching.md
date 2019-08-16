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