
# Remove untracked files (ignored or not)

- View files to be deleted: `git clean -f`
- To remove directories: `git clean -f -d` or `git clean -fd`
- To remove ignored files: `git clean -f -X` or `git clean -fX`
- To remove ignored and non-ignored files: `git clean -f -x` or `git clean -fx`

# Unstage files from rep & remove 

1, Unstage: `git reset filename.txt`
2. remove unstaged files 

## Undo `git add .`

`git reset`
 

# Stash 

- stash means temporary saving 
The `git stash` command takes your uncommitted changes (both staged and unstaged), saves them away for later use, and then reverts them from your working copy.

- 헤드 역시 뒤로 돌아간다는 점을 명시하자. 

## Reapply latest changes 

You can reapply previously stashed changes with `git stash pop` _Popping_  your stash removes the changes from your stash and reapplies them to your working copy.

Alternatively, you can reapply the changes to your working copy  _and_  keep them in your stash with  `git stash apply`.

https://www.atlassian.com/git/tutorials/saving-changes/git-stash




# Problem Solving 

## Q: Untrack files already added to git repository based on .gitignore


 http://www.codeblocq.com/2016/01/Untrack-files-already-added-to-git-repository-based-on-gitignore/





<!--stackedit_data:
eyJoaXN0b3J5IjpbMTIzNjQxNzEzMCwtMTUyMjYxMDUyXX0=
-->