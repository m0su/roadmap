# SSH
- Secure Shell의 약자.
- 네트워크의 다른 컴퓨터에 명령(로그인, 파일시스템 수정 등)을 실행하는 앱 또는 프로토콜.
- 22번 포트 사용
- 암호화 기법 사용 (통신이 노출되어도 암호화된 채로 노출됨)
- rcp, telnet, ftp 서비스들에 보안을 강화하고자 핀란드 개발자가 개발함
- 요즘은 AWS, git 등의 인스턴스 서버에 접속하기 위해 쓰임

### 동작
- Private Key와 Public Key의 쌍으로 구성되며, Private Key는 개인 로컬에, Public Key는 SSH로 접속할 컴퓨터에서 가지고 있는다.
- 상호 키 확인을 통해 인증된 사용자인지 확인한다.

### SSH 키를 이용한 git 계정관리
유닉스 시스템인 경우 ~/.ssh 디렉토리에 ssh 키를 보관한다.
```
# .ssh 폴더가 없다면 생성
mkdir .ssh

cd .ssh
ssh-keygen -t rsa -b 4096 -C "A계정 git이메일주소" -f "A계정 키-쌍 이름" # "id_rsa_A계정닉네임"
ssh-keygen -t rsa -b 4096 -C "B계정 git이메일주소" -f "B계정 키-쌍 이름" # "id_rsa_B계정닉네임"
# -t: 암호화방식
# -b: 키의 바이트 크기
# -C: github email

# ~/.ssh/conifg 경로에 추가
# A계정
Host github.com:A계정 닉네임
   HostName github.com  
   User A계정 닉네임
   IdentityFile ~/.ssh/id_rsa_B계정닉네임
   
# B계정
Host github.com:B계정 닉네임
   HostName github.com
   User B계정 닉네임
   IdentityFile ~/.ssh/id_rsa_B계정닉네임

# 연결 테스트
ssh -T git@github.com
```