### require & import
- require와 import는 외부 파일이나 라이브러리를 불러올 때 사용하는 `모듈` 키워드다.
- require는 `CommonJS`(Node의 모듈 문법)의 키워드고, import는 `ES6`에서 추가된 키워드다.
- ES6 사양을 지원하지 않는 환경이거나, Babel 과 같은 인터프리터가 없을 땐 require 을 사용해야 한다.

#### require
```javascript
//export 'requireTest.js'
  function moduleName() { ...code }
  module.exports = moduleName
//require
  const moduleName = require("./requireTest.js")
```

#### import
```javascript
// export 'importTest.js'
  function moduleName(){ ...code }
  export default moduleName; // 1. 단일 객체 모듈 export
  
  function module1(){ ...code }
  function module2(){ ...code }
  export module1; // 2. 복수 객체 모듈 export
  export module2; 
  // 혹은 합쳐서 export { module1, module2 };
  
// import
  import moduleName from "./importTest.js" // 1. 단일 객체 모듈 import
  import {Module1, Module2} from "./importTest.js" // 2. 복수 객체 모듈 import
```
#### 모듈 ?  
- 코드의 재활용성을 높이고 유지보수를 쉽게할 수 있도록 코드를 여러개의 파일로 분리하는 것 즉, 코드의 부품화라고 할 수 있다
- 특징
  - 자주 사용하는 코드를 필요할 때 마다 사용할 수 있다 `(재활용성)`
  - 하나의 모듈코드 수정을 통해 이를 이용하는 모든 코드를 제어할 수 있다 `(유지보수)`
  - 기능별로 세세하게 분업화 해놔서 코드 수정이 필요한 로직을 빠르게 찾을 수 있다 `(유지보수)`
  - 필요한 로직만 로드할 수 있기 때문에 `메모리의 낭비`를 막을 수 있다
  - 브라우저 환경에서는 한번 받은 모듈을 저장해두기 때문에 재활용을 통해 `네트워크 트래픽`과 `로직 로드 시간`을 절약할 수 있다
- JS에서는 모듈이란 개념이 분명하게 존재하지 않지만  
호스트환경(JS 구동 환경 = 브라우저, NodeJS...)에 따라 모듈화 방법이 존재한다
- 모듈을 언제든지 불러올 수 있도록 하는 시스템을 `모듈 시스템`이라 한다 
