# 문제 

- 원하지 않는 거대 파일이 git에 포함되었을 경우 이를 제거하는 방법 

# 요약 

https://rtyley.github.io/bfg-repo-cleaner 

# How to 

## Prerequisite 
- 자바를 실행할 수 있는 세팅이 되어 있어야 한다. 

## Process 
- 제거를 원하는 git의 하나 상위 디렉토리로 이동 
- 위 링크에서 <kbd>bfg</kbd>를 다운 받아서 해당 jar 확장자 실행파일을 해당 디렉토리에 놓는다. 
- 파일 이름을 bfg.jar로 바꾼다. 윈도에서는 git 확장자를 제거해야 한다. 

```
java -jar bfg.jar --strip-blobs-bigger-than 100M 지우고-싶은-git-이름 
```

- 해당 git 디렉토리로 다시 들어간다. 

```
git gc --prune=now --aggressive
```


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzMTkwNjc4NjFdfQ==
-->