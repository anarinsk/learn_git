# Source 

https://confluence.atlassian.com/bitbucketserver/using-forks-in-bitbucket-server-776639958.html
https://github.com/anarinsk/learn_git/wiki

# Concept 

기본적으로 포킹이란 공통작업을 하는 새로운 틀을 의미한다. 하나의 업스트림 리포가 있다고 하자. 이 업스트림 리포에 대한 공통 작업은 어떻게 진행되어야 하는가? 일단 생각할 수 있는 방식은 해당 리포를 협업자들끼리 클론한 후, 각자의 브랜치를 만들어 작업한다. 그리고 업스트림의 관리자가 해당 브랜치의 통합을 결정한다. 이는 복잡해질 우려, 그리고 브랜치 간의 잘못된 통합을 낳을 우려가 있다. 

때문에 나온 것이 `fork`다. 업스트림 리포를 내 개인 <kbd>remote</kbd>로 복사해온다. 이때 fork를 뜬 것은 특별한 이유가 없는 이상 일방향성을 갖는다. 즉, <kbd>remote</kbd>는 업스트림의 우위 아래에서도 두 리포의 내용을 서로 주고 받을 수 있다. 이때 forked repo의 내용을 업스트림으로 반영하는 절차, 즉 <kbd>forked</kbd> \rarr; <kbd>upstream</kbd> 방식을 Full Rquest라고 부른다. 


