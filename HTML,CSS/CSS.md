기본선택자
html의 head 영역에 style태그로 묶어서 표현한다
선택자를 정하고 중괄호로 묶은다음 각 스타일을 구현한다 (기본선택자, class선택자, id선택자)
    기본선택자 : 태그 (태그{내용})
    class : 그룹화 (.class명{내용})
    id : 단일화 (#id명{내용})
선택자를 중첩해서 범위를 좁힐 수 있다 (태그 class명 id명 {내용})
    * 콤비네이션 연산자 : 모든 태그에 각기다른 선택자를 부여하는것은 비효율적
    A B (Descendant selectors) : 
    A > B (Child selector) : 
    A + B (Adjacent sibling selector) : 
    A ~ B (General sibling selector) :
class나 id를 쓰지않고 각각 태그마다 적절한 이름을 쓰면 안되나?
    HTML에서 태그명에 의미를 부여하는 시멘틱태그를 참고하면 답이 된다. (컨벤션 준수)

