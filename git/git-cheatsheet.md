# Git
## Cheat Sheet

### Set up

**1. Initialize a git project**
```
$ git init project_folder
```

**2. Add remote (origin) with branch (master) to git repository and set upstream parameter**
```
$ git add remote origin master
```

### Frequent git workflow

**3. After each change add untracked file**
```
# of current directory to git
$ git add .

# of all changed & tracked files to git
$ git add -A
```

**4. Commit your changes**
```
# with a short message
$ git commit -m 'This is an example text'

# via Vim or another Texteditor (to benefit from using longer messages)
$ git commit

# short version (add & commit with a message at the same time)
$ git commit -am 'This is a commit message'
```

**5.a) Push the changes of a branch to your repository (e.g. origin)**
```
# with specifying remote, branch & parameter upstream (only at initial commit)
$ git push -u origin master

# with specifying remote and branch
$ git push origin master

# using previously set default upstream (remote = origin, branch = master)
$ git push
```

**5.b) Push the changes from your current branch to another remote and branch**
```
$ git push another_remote current_branch
```

**5.c) Push the changes to another remote using the same_branch_name as your co-workers (this way you add your changes to an already existing branch)**
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

**6. Make sure to be in the right branch. Get the latest changes from the remote (origin) and branch and merge them into your current local branch (Caution: if your tree is not clean, there might be merge conflicts here).**
```
$ git pull origin master
```

**7. Get a specific branch from a co-worker, checkout into it and track it as your newly created local branch**
```
$ git branch -t origin/yet_another_branch
```
