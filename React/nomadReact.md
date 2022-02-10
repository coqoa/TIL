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
---

### PropTypes

- prop의 타입을 지정할 수 있다 (코드상으론 에러가 아니지만 알맞지 않은 타입을 통해 로직이 꼬이는것을 방지)  
- 작성법
```javascript
Btn.PropTypes = {
	text : PropTypes.string
	fontSize : PropTypes.number
}
// 필수로 포함할 prop이면 .isRequired를  추가한다
```

### CRA (create-react-app)
- React 개발 편의성을 높여준다 (서버접근, 자동완성, css포함, 자동재실행, 경고메시지 발신 등등)
- npm으로 설치한다 (npm create-react-app)
---
1. src폴더에서 App.js, index.js빼고 모두 삭제  
2. index.js에서 작성되어 있는 3개의 import, ReactDOM.render빼고 모두 삭제  
3. App.js에서 function App내부(return내부에 `<div></div>`만 남기고 삭제)  
=>  사용하기 위해서 필요없는것들을 모두 정리해준다
---
- npm start : 실행


#### 컴포넌트 만들기
1. Button.js파일 만들어서 컴포넌트를 만들고 export해준다
```javascript
function Button({text}){
	return <button>{text}</button>;
}
export default Button
```

2. App.js에서 import
```javascript
import Button from "./Button"
```
2-1 사용할때는 ```<Button />```

#### propTypes설치 
1. npm prop-types
2. Button.js에 prop-types import
```javascript
import PropTypes from "prop-types"
```
3. 사용
```javascript
Button.propTypes = {
	text: PropTypes.string.isRequired
}
```

#### 특정 컴포넌트를 위한 css파일 생성
세가지 방법이 있다
1. css파일 만들기 : 전역적인 css스타일을 사용해야함
```javascript
	//index.js
    import "./style.css"
```
2. inline형태로 삽입하기  
   prop을 inline형태로 추가 : css의 장점이 사라짐
   
3. module.css 파일 만들기  : 위 두방법의 단점을 보완하면서도 장점이 있기 때문에 사용한다  
 -  Button.module.css파일 생성  
```css
/* Button.module.css 파일 생성 */
.btn{
	/*css내용*/
}
```   
- Button.js에 import (button에 className을 직접 지정하지 않고 styles.btn으로 사용)
```javascript
import styles from "./Button.module.css"
<button className = {styles.btn}>Button</button>  
```

=> 기존에는 html에서 식별자를 정하고 css를 바인딩해서 style을 꾸몄고 지금방법은 css의 이름을 html에 연결하는 식이다  
   이로인해 className은 랜덤한 값을 가지게 되었고 이는 다른 클래스 이름들을 사용하기 위해 기억하고 있는것 보다 효율적이다  
   why?  
   styles라는 이름으로 import하면 각 파일마다 styles.title을 사용해도 중복되지 않기 때문, 이름을 짓는데서 오는 어려움이 줄어듬,  
   소스코드에선 같은 코드라도 html에서는 각기 랜덤한 값을 받으므로 독립적으로 사용 가능

`+`CRA를 쓰면 더이상 `Reacr.`을 사용하지 않아도 된다 ( React.useState() => useState() )

### useEffect
- 언제 코드를 실행할 지 선택권을 가질 수 있는 코드
- 컴포넌트가 처음 실행될 때만 render 되는 것을 원할 수 있다 (ex. API를 통해 데이터를 가져올 경우 첫번째 컴퓨넌트 render에서 API를 콜하면 두번쨰부터는 가져올 필요가 없다)
- 하지만 React에서는 state가 변하면 rendering이 되고 이럴경우 useEffect를 사용하면 언제 코드를 얼마나 발생시킬지 선택권을 가질 수 있다

#### useEffect는 두가지 argument를 가지는 function이다
- 첫번째 argument는 실행하고 싶은 코드
- 두번째 argument는 특정 코드가 변경되면 첫번 째 argument를 실행하기 위한 dependency코드
- useEffect(실행할 코드, [dependency코드]
```
	useEffect(() => {
    	console.log('once')
    }, []);
```
#### dependency코드
- Array가 변할 때 useEffect의 첫번째 argument를 실행하는것이다
- []가 빈값이면 바라보는게 없으므로 최초 실행시 단 한번만 실행된다
- deps코드에는 여러가지 값이 들어갈 수 있다


### useEffect - CleanUp( )
- component가 destroy될 때 실행되는 코드다
- useEffect의 첫번째 argument return에 함수를 바인딩하면 된다 (= CleanUp function)
