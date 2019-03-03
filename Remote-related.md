Remote와 관련된 명령어들을 한번 정리해보자. 

# Remote location 

## remote
[LINK](https://help.github.com/articles/adding-a-remote/)

원격 저장소를 관리하는 명령어

- `git remote -v`: 현재 깃에 저장된 원격저장소 조회 
- `git remote add origin https://EXAMPLE.com`: remote 저장소로 origin이라는 이름의 저장소를 추가하며 주소는 https:이하 
- `git remote remove origin`: origin 원격 저장소를 삭제한다. 


# Remote &rarr; Branch 

Remote에서 local branch로 끌어오는 것과 관련된 명령어들 

## clone 

원격 리포를 통채로 당겨온다. 여러가지 작업을 동시에 수행한다. 

```cmd 
git clone https://github.com/USERNAME/REPOSITORY.git
```

- <kbd>repo</kbd> 이름의 하위 디렉토리 생성 
- git repo initializing 
- <kbd>origin</kbd>이라는 이름으로 원격 저장소 생성 
- 해당 원격 저장소 내용 다운로드 
- 다운받은 로컬의 branch이름은 <kbd>master</kbd>로 checkout 

## fetch 

## merge 

## pull 

# Push 
[LINK](https://help.github.com/articles/pushing-to-a-remote/)

로컬 브랜치에 스테이징된 내용을 원격 저장소로 밀어내는 명령어 

```cmd
git push  <REMOTENAME> <BRANCHNAME> 
```

- `git push origin master`: 현재 작업중인 git의 master branch를 origin이라는 저장소로 푸시한다. 
- `git push -u origin master`: -u 플래그는 `--set-upstream`의 약자. 이는 origin master를 기본 remote, branch의 대응쌍으로 두라는 이야기다. 


