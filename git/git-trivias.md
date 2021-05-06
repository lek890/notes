## Turn off git branch pager

git config --global pager.branch false

## Merge without switching branches

for forward merge

```
git fetch <remote> <sourceBranch>:<destinationBranch>

# Merge local branch foo into local branch master,
# without having to checkout master first.
# Here `.` means to use the local repository as the "remote":
git fetch . foo:master

# Merge remote branch origin/foo into local branch foo,
# without having to checkout foo first:
git fetch origin foo:foo

#for non fastforward
git fetch <remote> +<remoteBranch>:<localBranch>
```

https://stackoverflow.com/questions/3216360/merge-update-and-pull-git-branches-without-using-checkouts


remove and add new remote

git remote remove origin
git remote add origin <remote-name>
