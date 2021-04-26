# Modern JS

## 자바스크립트의 기원 
- 웹페이지에 상호작용을 손쉽게 적용하기 위해 1995년 탄생
- 규칙 제정 기관은 ECMA(European Computer Manufacturers Association)
- 변경은 누구나 제안할 수 있음
- 2015년 6월 크게 변경됨
  - 이는 ECMA6, ES6, ES2015 등으로 불림
- 이후 매년 ECMA(해당 년도)의 이름으로 버전이 개선

## ES6에서 변수 선언하기
- const
- let
  - 렉시컬 스코프 지원
- 템플릿 문자열
  - string interpolation
- 디폴트 파라미터
```javascript
  function Fun(parameter=defaultValue){
    ///...어쩌구
  }
```
## 화살표 함수
람다 노테이션을 쓸 수 있습니다

## ES6 트랜스파일링
모든 브라우저가 ES6 을 지원하지 않는다. 지원한다 하더라도 모든 ES6 문법을 지원하지 않을 수도 있다. 따라서 babel 과 같은 도구를 이용하여 이전 버전의 자바스크립트 코드로 변환한다. 

## ES6 객체와 배열
구조 분해(deconstruction)을 통해 필드 안의 값을 꺼내올 수 있다.
```javascript
  var sandwich = {
    bread:"더치 크런치",
    meat:"참치",
    cheese:"스위스",
    toppings:["상추","토마토","머스터드"]
  }
  var {bread, meat} = sandwich
```
### 구조 분해의 특징
- 구조 분해를 통해 꺼내온 값을 변경하더라도 원본 객체의 값은 변하지 않는다.
- 선언적이어서 코드를 작성한 사람의 의도를 더 잘 설명한다.

### 리스트 매칭
불필요한 값을 콤마를 이용하여 생략할 수 있다.
```javascript
var [firstResort]=["용평","평창","강촌"]
console.log(firstResort)//용평
```

```javascript
var [,,lastResort]=["용평","평창","강촌"]
console.log(lastResort)//강촌
```
## 객체 리터럴 개선
구조 분해의 반대
```javascript
var name ="탈락"
var elevation = 9738

var funHike = {name,elevation}
console.log(funHike)//{name:"탈락",elevation:9738}
```
함수를 리터럴 객체 생성에 넣음으로써 메소드를 추가할 수 있다.

## 스프레드 연산자
스프레드 연산자는 원본을 수정하지 않는다(Array.reverse와 같이 원본을 수정하는 연산자와 다름)

## promise
비동기 연산 처리를 위한 객체
```javascript
const promise1 = new Promise((resolve, reject)=>{
  setTimeout(()=>{
    resolve('foo')//resolve의 인자는 then 절의 콜백함수로 들어갑니다.
    },300
  )
})

promise1.then((value)=>{
  console.log(value)//"foo"
})
```

## 모듈
ES6에서 도입된 모듈을 통해 라이브러리나 외부의 자바스크립트 코드를 편하게 사용할 수 있다.
```javascript
export const print(message)=>log(message,new Date())

export const log(message,timestamp)=> console.log(`${timestamp.toString()}: ${message}`)
```
위의 코드는 두 함수를 외부에 공개한다.

하나의 이름만 외부에 공개할 때에는 `export default` 를 사용한다.  
`export default`를 통해 내보낸 모듈은 구조분해 없이 사용할 수 있고, 그렇지 않은 모듈은 구조분해를 이용하여 사용할 수 있다.  
`import *`를 통해 외부의 이름을 모두 로컬 이름 공간 안에 가져올 수 있다.

## CommonJS
모든 버전의 노드에서 사용할 수 있는 일반적인 모듈 패턴이다.  
커먼JS에서는 export를 사용할 때에 다음과 같이 사용할 수 있다.
```javascript
module.exports = {your,name,goes,here}
//import 는 다음과 같이 사용할 수 있다.
const {your,name,goes,here} = require("./file_name_goes_here");
```