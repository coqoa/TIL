# React

- 노마드코더의 React강의를 보고 혼자 정리하는 문서로 계속해서 변경될 예정이다

### JSX
JSX는 자바스크립트 확장문법이다.  
JSX를 사용하면 다음과 같은 장점이 있다.  
1. 데이터바인딩이 매우 편리해진다
2. HTML과 유사해서 익숙하며 보기 쉽다

### State
State는 변할 수 있는 데이터가 저장되는 곳이고 변하는 것을 보여주려면 다시 render해야한다.  
* render의 역할? root에 컴포넌트 하나를 담아주고 rendering해준다
* JS와의 차이점? React는 render할 때 변하는 부분만 업데이트 해준다
* 단점 ? render를 따로 써줘야 하므로 여기저기 난무하는 render함수덕에 시각적으로도 문제고 깜빡할 수 있으며 성능상 문제도 발생시킬 수 있다.  
* 단점을 해결하기 위해 ? useState를 사용한다
* useState 사용법 ? 
```javascript
// 1. function 내부(return의 상단)에 상수를 하나 만들고 React.useState(초기값);을 작성한다
const examUseState = React.useState(초기값);
// 2. console.log를 통해 examUseState를 출력하면 array를 반환한다. [초기값, function]
// 3. examUseState[0], examUseState[1]을 사용하는 방식은 가능하지만 불편하다.
// 4. 보편적으로 사용하는 방법은 다음과 같다.
const [data, setData] = React.useState();
```
useState의 두번째 인자로 받는 function(modifier function)이 필요한 이유?  
- state가 변하면 리랜더링 해준다
```javascript
const [counter, setCounter] = React.useState(0);
const onClick = () => {
  setCounter(counter+1);
}
return(
  <h1>Total clicks : {counter}</h1>
  <button onClick={onClick}>
  Click me !!
  </button>
)
```
- 데이터가 바뀌면 컴포넌트를 리렌더링하고 UI를 리프레쉬 (바뀌는 부분만)  

=> React를 사용하면 HTML요소를 생성, 검색할 필요도 없고 이벤트리스너 등록, UI 업데이트를 따로 할 필요가 없다

#### State function
* useState를 통해 state를 변경할 때 의도치 않게 변화가 생길 수 있다(같은값을 여러곳에서 사용한다거나..)
* 현재값을 통해 다음 값을 계산하도록 하면 좀 더 안전하게 사용할 수 있다
```javascript
setCounter((current) => current+1)
// 첫번째 argument는 현재값을 사용한다(어떤 이름이든 사용이 가능하다)
```

#### class, for같이 html에서는 사용가능하지만 JSX에서는 사용불가한 속성들이 있다
(ex. class => className, for => htmlFor)  

#### Input을 통해 입력값을 받을 때?
```javascript
onChange = (e) => {
  setValue(e.target.value)
}
```


### props
- 로직을 고립시켜서 분리된 컴포넌트를 만들고 export/import를 통해 사용한다 (캡슐화)  
- 부모컴포넌트로부터 자식컴포넌트로 데이터를 보내는것
- 각기다른 역할을 하는 버튼을 만들기 위해 각기 다른 컴포넌트를 만드는것을 비효율적


컴포넌트?  
어떤 JSX를 render하는 function  
props로 object를 보낼 수 있다  

사용법?  
function에 argument로 중괄호로 묶은 propsKey를 넣고 function 내부에서 사용한다, 여러개를 사용할 수 있다  
```javascript
function data({propsKey}){
  {propskey}
}
<Btn propsKey = propsValue />

```

### React.memo()

컴포넌트가 다시 그려지는 것을 원하지 않을때   
(ex. state가 변하지 않으면 다시 그릴 이유가 없음 - 성능저하의 원인이 되기도 한다)  
```javascript
// const Memorized = React.memo()

const MemorizedBtn = React.memo(Btn)
```
