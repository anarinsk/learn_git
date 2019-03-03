[https://help.github.com/articles/connecting-to-github-with-ssh/](https://help.github.com/articles/connecting-to-github-with-ssh/)

# macOS, ubuntu  

## rsa 키를 생성한다. 

* rsa키는 계정과 따라다닌다. 즉 linux에서 계정에 대해서 발급된다. 

```{}
ls -al ~/.ssh
```

키가 있는지 확인. 그런데, 왠만하면 새로 하나 만드는 것도... 숨은 파일이어서 안보인다면, `shift+command+.`를 눌러준다. 

```{}
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

일단 위의 명령어를 실행하면 `~/.ssh`를 생성해준다. 그러니 미리 디렉토리를 생성할 필요는 없다. 
계속 엔터를 쳐준다. 

## ssh 키를 ssh 에이전트에 넣어준다. 

```{}
eval "$(ssh-agent -s)"
```

에이전트 숫자가 할당된다. 

```{}
cd ~/.ssh
echo "Host *" > config
```

`nano config`를 해서 nano를 띄운 후 아래 파일을 적는다. 

```{}
Host *
 AddKeysToAgent yes
 UseKeychain yes
 IdentityFile ~/.ssh/id_rsa
```

```{}
ssh-add -K ~/.ssh/id_rsa
```

## Add id_rsa.pub to Github.com 

`github > settings > ssh ...`로 이동한다. 

터미널에서 

```{}
cat id_rsa.pub
``` 

키를 복사한 후 붙여 넣는다. 

## Test 

```{}
ssh -T git@github.com
```

잘 접속되는지 확인해본다. 

## How to use 

`https:\\`로 시작하는 대목을 `git@github.com:anarinsk/REPOSITORY`로 바꿔주면 되겠다. 

```{}
git clone git@github.com:anarinsk/REPOSITORY
```

