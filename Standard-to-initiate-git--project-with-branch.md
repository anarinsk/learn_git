# If not local dirs exists 

1. clone github dirs 
2. make repo and export to github repo 

가급적 매스터는 깨끗하게 유지하는 편이 좋겠다. 

# Make branch and switch to it 

1. At first, review your branch `git branch`
2. `git branch 새브랜치`
3. `git checkout 새브랜치`

# Make README.md and add & commit 

4. Make README.md by `echo "# 당신의 메시지" >> README.md`
5. git add -i 
6. git commit -m "커밋 메시지"

# Sync local repo to github repo 

```cmd 
git push --set-upstream origin 새브랜치 
```

- 명령어의 의미를 잘 이해하자. 
  1. 이 명령어는 upstream origin (현재 깃주소)에 <kbd>리모트 새브랜치</kbd>를 만들라. 
  2. 현재 <kbd>로컬 브랜치</kbd>를 <kbd>리모트 새브랜치</kbd>로 push하라. 

이 두 가지 작업을 동시에 수행한다. 

# If you want to start with github branch 

[Short and nice guide](https://gist.github.com/fabianmoronzirfas/4023446)

1. `git clone 깃헙리포`
2. `cd 로컬리포`
3. `git branch`

당연히 브랜치는 안 보인다. 추적 가능한 브랜치를 보고 싶다면, 

```cmd
git branch -a 
```

```cmd 
git checkout -b 갖고올브랜치 origin/갖고올브랜치
```

여기서 `git branch`를 해보면 <kbd>갖고올브랜치</kbd>로 체크아웃까지 되어 있다. 

`gitk --all &`을 쳐보자. 
