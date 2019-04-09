
```cmd
git reset --hard
git clean -f -d
```

# Description

Git Tips: Remove untracked files and directories from the working tree when switching branches or checking out different commits.

# Explanation

When switching branches or checking out another set of commits, you might want to only have the files and directories that are a part of that actual version. The commands shown above will accomplish this.

Be warned that any untracked files will be deleted, along with changes to tracked files. The two commands together reset the index and working tree, so ensure that any changes you don't want to lose were either committed to another branch or otherwise backed up somehow.

# Reference

`git reset --hard`

http://www.kernel.org/pub/software/scm/git/docs/git-reset.html

Resets the index and working tree. Any changes to tracked files in the working tree since <commit> are discarded. 

`git clean -f -d`

http://www.kernel.org/pub/software/scm/git/docs/v1.7.6/git-clean.html

`-d`
Remove untracked directories in addition to untracked files. If an untracked directory is managed by a different git repository, it is not removed by default. Use -f option twice if you really want to remove such a directory.

`-f` or `--force`

If the git configuration variable clean.requireForce is not set to false, git clean will refuse to run unless given -f or -n.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0OTkxMjE2MjhdfQ==
-->