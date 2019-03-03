# Format `.gitignore`

## Best case 

```cmd 
## RStudio Projects
.Rproj.user
.Rhistory
.RData
.Ruserdata

## MACOS generated files
*/.DS_Store
.DS_Store
.DS_Store?

## ipynb related 
.ipynb_checkpoints/

## Large files 
.csv 
.tsv 
```
# 3 ways to `.gitingnore` 

1. 리포 최상단에 `.gitignore` 
2. 리포 내 숨은 디렉토리 
  - `.git` > `info` > `exclude` 파일 안에 넣으면 된다. 
3. 글로벌 룰 설정 
  - `git config --global core.excludesfile ~/.gitignore_global` 
  - user/home에 `.gitconfig`가 생성 
  - 같은 디렉토리 안에 .gitignore를 넣으두면 모든 리포지터리에 대해서 적용된다. 

# How to apply newly made `.gitignore` 

일단 인덱스를 수정해줘야 한다. 그러기 위해서는 일단 

1. 현재 상태를 commit을 한다. (작업 상태 유지) 
2. 인덱스를 지운다. 

```cmd
git rm -r --cached .
```

3. 다시 add, commit을 반복한다. 


```cmd 
git add . 
git commit -m "YOUR_MESSEGE"
```
