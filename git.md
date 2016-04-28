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

## Merge
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


## Squash
**Squash** commits.  This means several commits are combined to look like 1 commit so the code history looks more tidy.
```bash
$ git reset --soft head~2    #2 is the number of previous commits to squash
$ git commit -v
$ git push <remote> <branchName>
$ git push <remote> +<branchName>    # add "+" symbol to force overwrite of remote git repo branch
```

## Remotes
Add an alias for a remote repo (eg. you want to push code to your fork before the main repo)
```sh
$ git remote add <alias> <url>      # add a git URL as alias
$ git fetch <alias>                 # download all branches from remote
$ git merge <alias>/<branchName>    # merge current branch with remote branch 
$ git push <alias> <branch>         # upload local branch commits to remote branch
$ git pull                          # fetch and merge commits from the tracking remote branch
```

##Stash
Save changes in current working directory, to work on another software feature.  

```sh
$ git stash save "feature1 WIP"
$ git stash list                    # show all stashed items
$ git checkout master               # remember to do $ git pull
$ git checkout -b feature2
... finish working on feature2 and go back to feature1 branch ...
$ git diff stash@{0}                # compare branch to stashed files
$ git statsh pop                    # merge stash with current branch
```
`git stash pop` will retrieve stashed files and merge with current branch.
You can also use `$ git stash branch <branchName>` to create a new branch from the stashed files.

