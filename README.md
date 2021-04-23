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

> github: https://github.com/settings/keys