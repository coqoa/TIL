### 기본선택자
- html의 head 영역에 style태그로 묶어서 표현한다 (css파일을 만들고 link로 묶어주면 따로 관리할 수 있다)  
- 선택자를 정하고 중괄호로 묶은다음 각 스타일을 구현한다 (기본선택자, class선택자, id선택자)  
```
    기본선택자 : 태그 (태그{내용})  
    class : 그룹화 (.class명{내용})  
    id : 단일화 (#id명{내용}) : 남발하면 안된다
 ```
- 선택자를 중첩해서 범위를 좁힐 수 있다 (태그 class명 id명 {내용})  
```
    * 콤비네이션 연산자 : 모든 태그에 각기다른 선택자를 부여하는것은 비효율적 (현실에서도 모든 사람들의 이름을 외우는 것은 불가능하므로 김씨의 셋째아들, 2반 반장 이런식으로 부른다)  
    A B (Descendant selectors) : 자손의 영역에서 찾는다  
    A > B (Child selector) : 자식의 영역에서 찾는다  
    A + B (Adjacent sibling selector) : 양 옆에 이웃한 범위의 선택자를 포함한다(형제선택자)  
    A ~ B (General sibling selector) : 이웃들의 범위를 한정한다 (형제들 중에서)  
    . 닷연산자 (class selector) : 자식이나 자손관계의 태그들의 범위를 좁힐 수 있다  
    (ul태그의 자손인 첫번째 li태그에도 first클래스가 있고 두번째 li태그에 포함된 a 태그에도 first클래스가 있다면li.first라는 선택자를 통해서 범위를 한정할 수 있다)  
    * 좀 더 복잡한 구조에서 한정사를 이용하려면 구조를 적어서 명확하게 구분 할 수 있다  
```
##### class나 id를 쓰지않고 각각 태그마다 적절한 이름을 쓰면 안되나?  
    HTML에서 태그명에 의미를 부여하는 시멘틱태그를 참고하면 답이 된다. (컨벤션 준수)  

### 속성 선택자  
```
선택자에 대괄호 [내용]을 추가해서 속성들을 선택자로 사용 할 수 있다  
선택자[속성선택자]{내용}  
```
추가내용 (많이쓰진않음)  
공백으로 구분된 선택자들 중 하나만 가지고 있어도 선택자로 사용하려면 [attr~=value]로 작성한다  
(div class = c1 c2 c3 c4 c5라는 속성을 가진 태그가 있다면  
[attr~="value"]라는 선택자를 통해서는 c1~c5 중 하나만 있어도 선택자로 사용할 수 있지만  
[attr="value"]라는 선택자를 통해서는 불가능하다(모든 속성을 가져야 선택자로 쓸 수 있으므로 [attr = c1 c2 c3 c4 c5]라고 작성해야 한다)  

[attr |= "value"] : 값이 참이면 출력 거짓이면 출력하지 않도록 할 수 있다  

[attr ^= "value"] : 속성값의 시작이 value로 시작하는 태그를 선택  
[attr $= "value"] : 속성값의 끝이 vlaue로 끝나는 태그를 선택  
[attr *= "value"] : value라는 값이 한번이라도 포함되어 있으면 선택  
[attr *= "value" i] : 소대문자를 가리지 않고 찾는다  
[attr |= "value" s] : 소대문자를 가려서 찾는다  
 
### FLEX
<container>로 <item/>감싸준다 - class가 container와 item을 필요는 없다, 자식과 부모가 있어야된다   
<container>의 속성 : display, flex-direction, flex-wrap, flex-flow, justify-content, align-items, align-content  
<item>의 속성 : order, flex-grow, flex-shrink, flex-basis, flex, align-self  

    
