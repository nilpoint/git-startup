# Git Startup
Learn git basics.

## Daily Howto

### How to get a specific branch from remote

If you haven't a work directory for that remote repository, you can use:
```bash
git clone -b [remote-branch-name] --single-branch <repository> [directory]
```
For example,

```bash
git clone -b 2.4 --single-branch https://github.com/opencv/opencv.git opencv-2.4

#or

git clone -b 2.4 --single-branch git@github.com:opencv/opencv.git opencv-2.4
```
**Note**

After cloning, you can't fetch any other branches. See .git/config:
```bash
git config --local --edit

[remote "origin"]
  url = git@github.com:user/repo.git
  fetch = +refs/heads/master:refs/remotes/origin/master
```
If you still want to get other branches, you have to change
```
fetch = +refs/heads/master:refs/remotes/origin/master
```
to
```
fetch = +refs/heads/*:refs/remotes/origin/*
```

If you already have a work directory for a remote repository, someone create 
and push a nwe branch. In this case, you need first fetch metadata from remote
repository:
```bash
git fetch origin
```
then
```bash
git checkout -b somebranch origin/somebranch
```
Finally, you can see all branches with:
```bash
git branch -a
```