# `non-fast-forward`errors 

## Problem  
Git이 push를 수행하고자 했으나 현재 커밋을 고치지 않고서는 푸시가 불가능할 때. 즉, remote의 버전이 현재 로컬이 작업버전보다 상위일 때 주로 발생한다. 

## Solution 

```cmd
git fetch origin
git merge origin YOUR_BRANCH_NAME
```

```cmd 
git pull origin YOUR_BRANCH_NAME
```