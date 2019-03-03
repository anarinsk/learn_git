# git 초기 세팅 사항들 

## 소용처 

  1. 컴퓨터를 처음 세팅했을 때 
  2. RStudio.cloud와 같은 데서 새 프로젝트를 론칭한 후 git setting을 잡아야 할 때 

## 필요 절차 

### 사용자 등록 및 이메일 등록 
```{}
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

### 최초 연동시 작업 진행 

```{}
echo "# TITLE_OF_YOUR_README.MD" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/anarinsk/YOUR_GIT.git
git push -u origin master
```

- echo는 " " 내용을 README.md 파일로 심어주는 역할이다. 
- git remote 계열의 명령어들은 좀 익혀두면 좋다. 

간편한 push, pull 작업을 위해서는 `git config --global push.default simple`

### github id/pw 관리 

```{}
git config credential.helper store
```
명령어 자체는 정보를 저장하라는 뜻이다. 
id/pw를 한번만 넣어주면 config에서 저장한다. 
