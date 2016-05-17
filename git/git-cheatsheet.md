# Git
## Cheat Sheet

### Set up

**1. Initialize a git project**
```
$ git init project_folder
```

**2. Add remote (origin) with branch (master) to the git repository**
```
$ git add remote origin master
# via SSH
$ git remote add origin git@github.com:1000miles/FIL.git

# via https
$ git remote add origin https://github.com/1000miles/FIL.git

# using another project_name
$ git remote add
```
**3. Clone an already existing repository**
```
# via SSH
$ git clone git@github.com:1000miles/FIL.git

# via SSH including renaming project root folder (FIL => my_app)
$ git clone git@github.com:1000miles/FIL.git my_app

# via https
$ git clone https://github.com/1000miles/FIL.git

# via https changing the project root folder name (FIL => my_app)
$ git clone https://github.com/1000miles/FIL.git my_app
```

### Frequent Git workflow

**4. After each change add untracked file**
```
# of current directory to git
$ git add .

# of all changed & tracked files to git
$ git add -A
```

**5. Commit your changes**
```
# with a short message
$ git commit -m 'This is an example text'

# via Vim or another Texteditor (to benefit from using longer messages)
$ git commit

# short version (add & commit with a message at the same time)
$ git commit -am 'This is a commit message'
```

**6.a) Push the changes of a branch to your repository (e.g. origin)**
```
# with specifying remote, branch & parameter upstream (only at initial commit)
$ git push -u origin master

# with specifying remote and branch
$ git push origin master

# using previously set default upstream (remote = origin, branch = master)
$ git push
```

**6.b) Push the changes from your current branch to another remote and branch**
```
$ git push another_remote current_branch
```

**6.c) Push the changes to another remote using the same_branch_name as your co-workers (this way you add your changes to an already existing branch)**
```
$ git push another_remote same_branch_name
```

### Helpful Commands

**1. List all your local remotes**
```
$ git remote -v
```

**2. List all your local branches**
```
$ git branch -v
```

**3. List all existing branches that are associated with the original remote and branch, means also from your co-workers.**
```
$ git branch -r
```

**4. Make sure to be in the master branch. Create another local branch and switch into the newly created branch.**
```
# longer version:
$ git branch new_branch
$ git checkout new_branch

# quick version:
$ git branch -b new_branch
```

**5. Make sure to be in the right branch. Fetch the latest changes from the original remote and branch into your current branch without modifying the files of your local branch.**
```
# from master
$ git fetch origin

# from a specific branch
$ git fetch origin branch_name
```
**6.a) Make sure to be in the right branch. Merge the latest changes from another branch into the current branch**
```
$ git merge fetched_branch
```

**6.b) Make sure to be in the right branch. Get the latest changes from the remote (origin) and branch and merge them into your current local branch (Caution: if your tree is not clean, there might be merge conflicts here).**
```
$ git pull origin master
```

**7. Get a specific branch from a co-worker, checkout into it and track it as your newly created local branch**
```
$ git branch -t origin/yet_another_branch
```

**8. Show all your commits in the current branch**
```
$ git log
```

**9. Show all the references of your activities log**
```
$ git reflog
```

**10. Show the difference**
```
# of all files in the current branch:
$ git diff

# of a specific file in a branch:
$ git diff filename.rb

# of files from your local branch against your local master branch:
$ git diff current_branch master

# of files from your local branch against the remote (origin) and master branch:
$ git diff current_branch origin/master
```
**11. Store your not yet committed changes from a branch when you need to work on another branch suddenly**
```
$ git stash
```

**12. Show all stash changes of a branch**
```
$ git stash list
```
**13. Get back your stashed changes when you need to continue your previous work**
```
# last stashed reference
$ git stash pop

# a specific stashed reference
$ git stash pop reference_code
```
**14. Stash commits of two branch into one commit and one branch**
```
$ git stash branch <branchname> [<stash>]
```

## Troubleshooting

**1. Reset your last committed change so that the files in the git tree become untracked again**
```
$ git reset HEAD
```

**2. Remove files from the untracked tree**
```
# checkout a single file
$ git checkout file.rb

# checkout multiple files at the same time
$ git checkout file.rb another_file.rb yet_another_file.rb

# checkout the current directory
$ git checkout .
```

**3. Rebase your commits interactively when you have merge conflicts**
```
$ git rebase -i branch_name
```

**4. Pickup a commit of the current branch selectively**
```
$ git cherry-pick commit_number
```
**5. Move on to the next cherry-pick of a commit**
```
$ git cherry-pick --continue
```

**6. Revert a specific commit**
```
$ git revert commit_number
```

**7. Clean your branch by removing all changes**
```
# remove untracked directories additionally to untracked files (Caution!)
$ git clean -d

# show only what would be removed but don't remove actually
$ git clean -n
or:
$ git clean --dry-run

# force to clean (Caution: it will remove all files completely without displaying any warnings)
$ git clean -f
```
