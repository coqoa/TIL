생활코딩 GIT-CLI-버전관리 수업을 듣고 정리합니다.  
[https://opentutorials.org/module/3762](https://opentutorials.org/module/3762)

## GIT CLI 버전관리
    비교를 통해 과거를 볼 수 있음

 - git init (initialize) - 로컬 깃 저장소로 등록
 -  git status - git의 상태체크

## 버전만들기
# Working Tree | Staging Area | Repository 

 - working tree : 파일을 수정하는곳, 수정한 파일들
 - Staging Area : 버전을 만드려는 파일들 (커밋하려는 파일들)
 - Repository : 만들어진 버전(커밋)

1. 파일생성 / 변경, WorkingTree
2. git add, Staging Area에 올림
 > git add 파일명(확장자포함) : 파일(Working Tree의 수정사항)을 Staging Area에 올린다
3. git commit, Repository등록
 >  git commit -m "커밋메시지" : Staging Area에 올려진 파일을 Repository로 커밋한다

## 버전간의 차이점 비교 
 - git diff : 버전간의 차이점을 비교
 - git log -p : 어느부분에서 문제가 생겼는지 추적할 수 있음
## checkout과 시간여행
 - git checkout 커밋ID : 커밋ID가 가지는 버전을 만든 시점으로 돌아간다 (삭제되는건 아님)
    - 커밋ID는 git log를 통해 확인가능
 - git checkout master : 가장 최신이었던 상태로 돌아간다

## 보충설명
 - git add . : 디렉토리에 있는 모든 파일을 add한다
 - git add 디렉토리명 : 해당 디렉토리의 모든 파일을 add 한다
 - git commit -m "커밋메시지" : 커맨드라인에서 직접 커밋메시지를 작성할 수 있다.
   - git commit 만 작성시  기본에디터를 실행하고 여러줄의 커밋메시지를 입력할 수 있다
 - git commit -am "커밋메시지" : add와 commit을 한번에 한다
    (최초한번은 add를 통해 tracked상태가 되야 가능한 방법)
 - git config --global core.editor "nano" : nano를 기본에디터로 설정

## 삭제
- git reset --hard 커밋ID : 커밋ID의 '버전으로' 되돌린다. (해당 버전이후의 버전은 삭제된다)
  -  --hard의 뜻 : 버전, 수정중인 파일 등 모두 지운다

## 되돌리기
- git revert 커밋ID : 커밋ID 이전의 버전으로 되돌린다 (ex. 3번으로 돌아가고싶으면 4번의 커밋ID를 사용)
    > git revert 커밋ID  입력하면 기본에디터가 켜지고 저장 후 나오면 적용됨  
    > 기존의 커밋은 남겨두고 해당 커밋에서 의 변화를 취소하는식으로 처리가됨 (이전의 버전으로 되돌아감)  
    > 단계를 건너뛰어서 revert하면 conflict발생한다 -> 이유 ? 해당 커밋만의 상태를 되돌리므로  
    >  (1,2,3,4중 1로 가기위해 2를 revert하면 1,3,4가 남은 상태가 되므로 conflict발생)  

     [https://coqoa.tistory.com/47](https://coqoa.tistory.com/47)
