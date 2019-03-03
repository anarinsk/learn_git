# Source 
- http://webclub.tistory.com/317
- http://ryujek.tistory.com/entry/Git-%EB%AA%85%EB%A0%B9%EC%96%B4
- [Stash](http://wit.nts-corp.com/2014/03/25/1153)

# Meta 

- 여기서 로컬이란 내 컴퓨터의 저장소를 의미한다. 
- 버전 관리를 위해서는 로컬에서부터 이를 위한 작업 및 단계 정의가 필요하다. 

# Basic concepts 

![](https://git-scm.com/figures/18333fig0106-tn.png) 
![](https://t1.daumcdn.net/cfile/tistory/2171D43E56ADC9F018) 

## working directory : <kbd>wd</kbd> 
- 로컬 파일들로 구성된 작업 공간  

### File status 
1.  <kbd>tracked</kbd>
  - unmodified, modified, staged
2. <kbd>untracked</kbd>

## staging area : <kbd>index</kbd> 
- 워킹 디렉토리의 수정 사항 중에서 나중에 커밋을 위해서 빼둘 파일들을 지정 
- 명령어: `add`
## commit : <kbd>HEAD</kbd> 
- staging area의 내용을 실제로 로컬 파일로 확정하는 최종 확정본을 의미 
- 명령어: `commit`

처음에 클론했을 경우 모든 파일은 tracked + unmodifed 상태 

# Walk-through by git command 

## status 
- 현재 wd의 상태를 파악한다. 

```cmd
> git status
On branch master
On branch master nothing to commit, working directory clean
```

- 현재 <kbd>master</kbd> 브랜치에 있다. 
- 이 브랜치에 현재 커밋할 내용이 없고(즉 스테이징된 내용이 없고), 워킹 디렉토리에서도 변경된 것이 없다. 

## add 
- <kbd>wd</kbd> &rarr; <kbd>index</kbd>. Make selected files to be staged. 
- `git status`로 확인해보면 다음과 같다. 

```cmd
> git add README
git status 
On branch master Changes to be committed: 
  (use "git reset HEAD ..." to unstage) new file: README
```

## commit 
- <kbd>index</kbd> &rarr; <kbd>HEAD</kbd>. Make files in the index to be committed 

```cmd 
git commit -m "변경된 메시지 내용을 입력"
```

- add & commit 

```cmd 
git commit -am "변경된 메시지 내용을 입력"
```

## rm 
- <kbd>index</kbd> &rarr; <kbd>wd</kbd> 
- wd의 파일도 지워진다!
- 만일 `rm`으로 지우지 않고 그냥 폴더, 디렉토리에서 지웠다면? 
  - `git status`로 확인해보면, 이 경우는 unstaged 상태가 된다. 즉, <kbd>index</kbd>에 올라가지 않는 파일이 삭제되어 버린 것이다. 따라서 제대로 commit을 진행하려면 indexing이 되어야 한다. 

### cached 
- 해당 파일을 staging area에서만 제거하고 워킹 디렉토리에 그대로 남겨두고 싶다면? 
- 이는 `.gitignore`에 파일을 추가하는 것을 빼먹었거나 불필요한 대용량 파일들을 실수로 추가했을 때 사용할 수 있다. `--cached` 옵션을 사용하면 된다. 

```cmd 
> git rm --cached readme.txt
> git rm log/\*.log
> git rm \*~
```

- <kbd>index</kbd>에서 readme.txt 파일을 <kbd>index</kbd>에서 제거한다. 
- <kbd>index</kbd>에서 `log/` 디렉토리의 `*.log` 파일들을 제거한다. 
- ~로 끝다는 파일들을 제거한다. 

## push 
- <kbd>HEAD</kbd>에 마지막으로 commit된 사항을 remote git repo에 저장한다는 의미

```cmd 
> git push - u origin master
```

- origin 이라는 이름의 remote repo로 master 브랜치의 내용을 밀어내라는 이야기 
- `-u` 옵션은 remote repo의 내용을 업데이트한 후에 push를 하라는 이야기 
- 저장소를 사용한 사람이 여러 명일 경우, 혹은 1명이 여러 머신을 오가며 작업할 경우 다른 사람이 push를 한 이후에는 내가 push할 수 없다. 왜냐하면 스냅샷의 내용이 달라서 완결성을 보증할 수 없기 때문이다. 이 경우 다른 사람의 작업을 가져와서 merge한 후에 push할 수 있다. 

# Undo 
- 일종의 되돌리기(undo)개념이다. 
- git에서 commit한 것은 언제든지 되돌릴 수 있다. 하지만 commit하지 않은 것은 되돌릴 수 없다. 

## <kbd>HEAD</kbd> &rarr; <kbd>index</kbd>: amend 
- 얘는 <kbd>HEAD</kbd> 즉 committed files에 대해서 수행하는 작업이다. 
- 즉, <kbd>HEAD</kbd> &rarr; <kbd>index</kbd> 내린다. 
- 만일 마지막으로 커밋한 후 수정한 것이 없다면 메시지만 수정하면 된다. 
- 커밋을 했는데 스테이지를 못한 파일이 있다면 이 명령어를 쓰면 된다. 

```cmd
git commit -m 'initial commit' 
git add forgotten_file 
git commit --amend
```

- 이렇게 되면 모두 하나의 커밋으로 취급된다. 두번째 커밋은 첫번째 커밋을 덮어쓰게 된다. 

## <kbd>index</kbd> &rarr; <kbd>wd</kbd>: reset HEAD

> 예를 들어 파일을 두 개 수정하고서 따로따로 커밋하려고 했지만, 실수로 git add * 라고 실행해 버렸다면 두 파일 모두 Staging Area에 들어가 있을 것입니다. 

- `git status`를 치면 필요한 명령어를 보여준다. 

```cmd 
git add . 
git status 
On branch master Changes to be committed: 
  (use "git reset HEAD ..." to unstage) 

  modified: README.txt 
  modified: benchmarks.rb
```

```cmd 
git reset HEAD benchmarks.rb 
Unstaged changes after reset: 
M benchmarks.rb
```
- benchmarks.rb를 다시 index에서 꺼내서 working directory로 던진다. 즉, unstage 
- 확인을 위해서 `git status`를 다시 때려본다. 

```cmd
git status 
On branch master 
Changes to be committed: 
  (use "git reset HEAD ..." to unstage) 

    modified: README.txt 

Changes not staged for commit: 
  (use "git add ..." to update what will be committed) 
  (use "git checkout -- ..." to discard changes in working directory) 
    modified: benchmarks.rb
```

## <kbd>wd</kbd> &rarr; recently committed: checkout 

<kbd>wd</kbd>에서 작업하던 내용이 마음에 안 든다. 그래서 다시 원래 초기 상태로 돌아가고 싶을 때, 역시 `git status`를 때려본다. 

```cmd
Changes not staged for commit: 
  (use "git add ..." to update what will be committed) 
  (use "git checkout -- ..." to discard changes in working directory) 

    modified: benchmarks.rb
```

```cmd 
git checkout -- benchmarks.rb 

git status 
On branch master 
Changes to be committed: 
  (use "git reset HEAD ..." to unstage) 

    modified: README.txt
```

- 이는 위험한 명령이기도 하다. 이렇게 해 두면, 수정 이전의 파일로 덮어쓴 셈이고, 따라서 수정 버전으로 돌아갈 수가 없다. 
- commit된 내용은 복원이 가능하지만 그렇지 않은 내용에 대해서는 복원이 불가능한 셈이다. 

# Stash

