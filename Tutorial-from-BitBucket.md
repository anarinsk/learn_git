# Cheat Sheet 

[https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet](https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet)

# Setting up 

## `git init` 

### `--bare` vs non-bare 

`--bare` 플래그가 붙으면 해당 영역에서는 오직 push나 pull만 가능하다. 즉, 이 스토리지는 개발을 위한 행위(add, commit)등은 불가능하다. 즉 bare flag로 만든 git은 오직 소스 저장소 역할만 한다. 

## `git clone`

몇가지 유용한 명령어를 기억해두자. 

```{git}
git clone -depth=1 <repo>
```

가장 최근에 커밋된 깃만을 가져온다. 

```{git}
git clone -branch new_feature git://remoterepository.git
```

`new_feature` 브랜치를 카피해온다. 일반적인 구조로 사용하면  `master` branch를 복사해온다. 

## URL protocols 

깃헙 기준으로 설명하자. 

  1. ssh `git clone ssh://git@github.com:anarinsk/repo.git`
  2. git `git://host.xz[:port]/path/to/repo.git/`
  3. http(s) `http[s]://host.xz[:port]/path/to/repo.git/`


# Saving 

## `git add` 
## `git commit` 
## `git diff` 
## `git stash` 
## `.gitignore`

# Inspecting 

## `git status`
## `git tag`
## `git blame`

# Undo 

## `git checkout`

```{git}
git checkout a1e8fb5
git checkout master
```

기본적으로 체크아웃은 커밋포인트 혹은 브랜치로 이동해 나가는 것을 의미한다. 
만일 대상으로 파일이 온다면 해당 파일의 스테이징을 취소하는 것이다. 

`master`를 제외하면 쳌아웃을 하게 되면 "detached HEAD" 상태가 된다. 즉, HEAD가 떨어져 나간 상태로서 이 상태에서 저장된 것이나 commit된 것을 별도로 고립되고 git이 다시 시작할 때 gc(garbage collector)에 의해 회수되어 사라잔다. 그래서 이 이후부터 작업을 하고 싶다면 반드시 새로운 브랜치를 열어여 한다. 

```{git}
git checkout -b new_branch_without_crazy_commit
``` 

이렇게 되면 쳌아웃하게 된 커밋은 사라진다. 그리고 당연히 이 커밋 하위에 붙어 있던 커밋들도 없어지게 된다. 

## `git clean`

untracked files을 지우는 명령어이다. untracked files이란 작업 리포에서 생성되거나 수정되었으나 아직 `git add` 명령을 통해서 스테이징되지 않은 파일을 의미한다. 

```{git}
git clean
```

안전상 이 명령어는 듣지 않는다. 

```{git}
git clean -n
git clean -f
```

"dry run" 옵션이다. 실제 지우지는 않고 어떤게 지워지는지 확인한다. `-f`는 실제로 지운다. 

```{git}
git clean -df 
```

`-d` 옵셥은 미추적 디렉토리까지 날리라는 이야기 

```{git}
git clean -xf 
```

ignore 처리된 파일을 지우라는 이야기 

```{git}
git clean -di
```

인터렉티브하게 지우라는 이야기다. 

## `git revert`

그림으로 한마디로 설명하면 다음과 같다. 

![](https://www.atlassian.com/dam/jcr:b6fcf82b-5b15-4569-8f4f-a76454f9ca5b/03%20(7).svg)

즉, 이전 커밋(`~x`)을 맨 앞으로 끌고 와서 새 커밋으로 만드는 것을 의미한다. 

```{git}
git revert HEAD~x
```

`reset`과 유사하지만 몇 가지 장점을 지니고 있다. 

## `git reset`

# Rewrite History 

#