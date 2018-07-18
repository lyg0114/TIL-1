# Linux SysAdmin Basics
>[tutoriaLinux](https://www.youtube.com/watch?v=bju_FdCo42w&list=PLtK75qxsQaMLZSo7KL-PmiRarU7hrpnwK) 유튜브 영상으로 학습하며, 익숙하지 않은 명령어들 정리

## 1. Basics
- `rmdir 디렉토리명` 디렉토리 삭제
  - 디렉토리가 비어있지 않을 경우 `rm -r 디렉토리명`으로 삭제
- `ctrl + a` = 명령 첫부분으로 가기
- `ctrl + e` = 명령 끝부분으로 가기
- `ctrl + r` = 이전 명령어 검색
- `ctrl + c` = esc 역할
- `ln -s File linkFile` 링크 만들기
  - 링크파일에서 내용 수정하면 원본파일 내용도 수정된다.
- `shutdown -r` = restart
  - `shutdown -h now` = halt now
  - `shutdown -h +60` = 한시간뒤에 종료
- `w` 또는 `who` = 사용자들 확인
- `mkdir -p 경로1/경로2/경로3...` = 여러 단계의 경로 생성
  - `rm -r 경로1` = 경로 삭제 (경로 안의 모든 경로 삭제)
- `cp`  = 파일 복사

## 2. Shell Features -- Pipes and Redirection

### Redirection
>standard in = 0  
>standard out = 1  
>standard error = 2

- `echo "this should be in a file" 1> somefile.txt` = 파일생성하면서 내용 넣기 (1 생략 가능)
- `echo "this should be line 2" >> somefile.txt` = 파일에 내용 추가
- `ls -alh somfile.txt >> list.txt` = list.txt 파일 생성하면서 `ls -alh somefile.txt` 명령의 결과를 내용으로 넣기
- `ls -alh someeflajdfaldkjfw 2> err.txt` = `ls -alh some someeflajdfaldkjfw`명령의 결과(에러 메세지)를 err.txt에 넣기
- `echo "this is the message text" > message.txt`,  
`mail -s "this is the subject" ryan < message.txt` = message.txt 파일의 내용을 "제목"의 제목으로 ryan에게 보내기

### Pipe
- `A | B` = A의 결과를 B에 넣는다.
  - ex) `ps aux | less`
- `prog1 | prog2 | prog3` = prog1의 결과를 2에 넣고 2의 결과를 3에 넣는다.
- `prog1 && prog2` = prog1 명령이 성공이면 prog2 명령 실행
  - ex) `ls file.txt && echo "astonishing success."`

- `cat file.txt`
    ~~~
    ryan:we  
    user:love  
    someone:linux
    ~~~
- `cat file.txt | cut -d: -f2`
    ~~~
    we
    love
    linux
    ~~~