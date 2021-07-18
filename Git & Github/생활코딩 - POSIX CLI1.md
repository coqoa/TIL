생활코딩 POSIX CLI1 수업을 듣고 정리
 
# GIT POSIX(portable operating system interface)
시간의 순서에 따라 명령을 내릴 수 있다

## 단축키
- pwd : 현재나의위치 (print working directory)
- ls : 파일목록보기
- cd : 디렉토리 이동 (change directory)
- cd / : 최상위 디렉토리로 이동
- cd /users/coqoa : users/coqoa으로 이동 : home directory
- man ~~ : 사용설명서 보기 : command manual (ex. man ls : ls의 사용설명서 보기)

# Directory 관련 단축키
- mkdir 파일이름 (make directory) : 디렉토리만들기
- mv 파일이름 바꿀이름 : 이름바꾸기 (move)
- rm -r 파일이름 : 삭제하기 (remove)

## 참고사항 
- ls -l (상세정보확인)
- ls -a (히든파일확인)
-  -> 합쳐서 ls -al 혹은 ls -la로 사용가능

- touch 파일만들기
- .filename : 히든파일만들기
- ./ : current directory
- ../ : parent directory
-  * ( ./posix : 현재디렉토리의 posix , /posix : 최상위디렉토리 밑의 posix , .posix : posix라는 이름의 히든파일)

- cd / -> 절대경로사용 (어느위치에서나 갈 수 있는 경로) (ex. cd ./posix)
- cd../ -> 상대경로 사용 (나의 위치에 따라 결과가 다른 경로) (ex. dc /users/coqoa/posix)

# File 관련 단축키
- 생성 : nano라는 텍스트에디터 사용
  - nano hello1.txt
  - nano editor 내부에서 |^o : ctrl + O, ^x : ctrl + x|
  -- cat hello1.txt
  --- 읽기 : nano hello1.txt 혹은 cat hello1.txt (cat은 화면에 출력하고 끝나는 명령어다
- 파일수정과 삭제
 > mv 파일이름 바꿀이름 : 이름변경 (ex. mv hello.txt hello_world.txt)
 > mv hello_world.txt ../hello_world.txt : 파일 이동
 > rm hello_world.txt : 파일삭제 (디렉토리와는 다르게 -r 사용하지않는다)
- ;대신 &&을 쓰면 오류시 자동화를 종료해준다
