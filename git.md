# Git 
Frequently used
```bash
$ git checkout -b <newBranchName>   # remember to first checkout master branch
$ git checkout <branchName>
$ git checkout -- <filename>
$ git log -p
$ git log --oneline
$ git status
$ git diff
$ git diff <fileName>
$ git diff --staged
$ git add <fileName>
$ git stash
$ git commit -v 
$ git remote -v
$ git push <remoteName> <remoteBranchName>
$ git push <remoteName> <localBranchName>:<remoteBranchName>
$ git pull <remoteName> <remoteBranchName>
```

**Merge** branches that have conflicts
```bash
$ git checkout -b <newBranch>
$ git merge <branch1> <branch2>
$ git diff    #or use git mergetool
... now proceed to resolve branch conflicts using editor (eg. vim, eclipse, atom)...
$ git add <fileName>
$ git commit -v
$ git push <remoteName> <remoteBranchName>
```



**Squash** commits.  This means several commits are combined to look like 1 commit so the code history looks more tidy.
```bash
$ git reset --soft head~2    #2 is the number of previous commits to squash
$ git commit -v
$ git push <remote> <branchName>
$ git push <remote> +<branchName>    # add "+" symbol to force overwrite of remote git repo branch
```



