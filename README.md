# ssh키 등록
## windows
> $ ssh-keygen -t rsa
> > Generating public/private rsa key pair.  
> > Enter file in which to save the key (/c/Users/choi/.ssh/id_rsa):**[enter입력]**  
> > Created directory '/c/Users/choi/.ssh'.  
> > Enter passphrase (empty for no passphrase):**[비밀번호 입력]**(enter입력 시 비밀번호 없이 사용)  
> > Enter same passphrase again:**[비밀번호 확인]**  

비밀번호 확인까지 입력 완료 되면 키 파일 다음 경로에 생성 됨 
> C:\Users\[user_name]\.ssh\id_rsa.pub
해당 파일 메모장으로 열어서 복사 후 git사이트에서 ssh키 등록

## linux
ssh-keygen -t rsa

> github: https://github.com/settings/keys

# git 운용 관련
## 1. pull-request 기반 운용 시 git account 관리
git account는 회사 계정, 각 사원별 계정이 필요

## 2. git repository
회사 계정에 repository생성 후 각 작업자들이 회사 계정에 생성 한 repository를 
fork해서 사용

## 3. fork한 repository에서의 setting
- fork로 인해 복사 된 본인 계정의 repository를 clone.
- git remote add upstream https://github.com/[ORIGINAL_OWNER]/[ORIGINAL_REPOSITORY]

## 4. 작업내용 추가
> 작업 내용을 추가 할 때는 main을 checkout한 후 branch생성. 해당 branch에 작업내용 추가.
- git branch [branch name]
- git add -p [file name]
- git commit -m "comment"
- git push origin [branch name]

## 5. Pull-request작성, code review
- git web site에서 fork한 브런치 화면을 열고 Pull-request작성
- reviewer가 해당 코드를 리뷰, 코멘트 작성
- review완료 후 권한이 있는 작업자가 Original repository에 merge진행

## 6. original, fork repository동기화
> review완료 후 original에 merge되면 fork해둔 repository에는 반영 안 된 상태이므로 동기화 필요
- git fetch upstream
- git checkout main
- git rebase upstream/main

## 7. alias(.git/config)
```
[alias]
        git config --global alias.co checkout
        git config --global alias.rb "rebase -i"
        git config --global alias.st status
        git config --global alias.cm commit
        git config --global alias.pl pull
        git config --global alias.ps push
        git config --global alias.lg log "--graph --abbrev-commit --decorate --format=format:‘%C(cyan)%h%C(reset) - %C(green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(yellow)%d%C(reset)’ --all"
        git config --global alias.ad add
        git config --global alias.tg tag -n
        git config --global alias.df diff
        git config --global alias.br branch
```
## 8. Pull-request를 위한 main push 방지 설정
> Pull-request를 사용하지 않고 main에 직접 push하는 케이스를 방지하기 위한 설정. (이미지의 빨간 박스 참조)

![image](https://user-images.githubusercontent.com/83071973/124046771-af1a3780-da4d-11eb-9710-a08a9ab37964.png)
