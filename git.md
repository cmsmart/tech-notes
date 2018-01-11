
# Git

## Change the remote

```git remote set-url origin https://github.com/<yourgithubrepo>```


## Branching

### View all branches
``` git branch -a ```

### Clone a specific git branch

```git clone -b <branch> <remote_repo>```

### Pull down a specific branch

```git fetch <remote_repo> <remotebranch>:<localbranch>```

### Create and use a specific branch

``` git checkout -b <branchname> ```

### Switch branches

``` git checkout <branchname> ```

### Show remote branches

``` git remote show origin ```

### Checkout remote branch

``` git checkout --track origin/remote_branch ```

which is the same as 

``` git checkout --track -b [branch] [remotename]/[branch] ```

### View diff

``` git diff origin/master..HEAD ```

### Checkout a new remote branch that doesn't exist on local

``` git fetch origin ```
``` git checkout --track origin/<remote_branch_name> ```