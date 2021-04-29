# 순수 리액트

jsx를 트랜스파일하면 생기는 코드는 순수 리액트 코드

## 페이지 설정
리액트를 브라우저에서 사용하기 위해서는 다음의 라이브러리가 필요하다
- React
  - 뷰를 만들기 위한 라이브러리
- ReactDOM
  - 렌더링할때에 사용되는 라이브러리

리액트로 작성한 html 문서 설정
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>pure react example</title>
  </head>
  <body>
    <div class="react-container"></div>
    < src="https://unpkg.com/react@16/umd/react.development.js"></>
    < src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></>
    <>
      //순수 리액트 코드
    </>
  </body>
</html>
```
## V-DOM
가상DOM은 리액트 엘리먼트로 구성되는 자바스크립트 코드이다.
V-DOM을 통해 DOM을 조작하는 것이 그냥 DOM을 다루는 것보다 훨씬 빠르다.

## React Element
react element로 h1 태그 생성하기
```javascript
React.createElement("h1",null,"text")
```
위 코드의 인자의 순서는 다음과 같다.
- 태그명
- 애트리뷰트
- 자식 노드
  
이 코드는 다음의 실제 DOM으로 변환된다.

```html
<h1>text</h1>
```

애트리뷰트가 있는 React Element는 다음과 같이 지정할 수 있다.
```javascript
React.createElement(
  "h1",
  {id:'sample-id','data-type':'title'},
  text
)
```

리액트 엘리먼트는 DOMElement를 구성하는 방법을 기술한 리터럴일 뿐이다.

## ReactDOM
ReactDOM에는 리액트 엘리먼트를 구성하는 기본적인 도구들이 있다.
이는 다음의 메소드를 포함한다.
- render
- renderToString
- renderToStaticMarkup

위의 메소드들은 12장에서 자세히 다룬다.

리액트에서는 화면에 엘리먼트를 그리기 위해 `ReactDOM.render`를 사용한다. 이 함수의 첫번째 인자는 렌더링할 리액트 엘리먼트이며, 두번째 인자는 렌더링이 일어날 DOM 노드다.

```javascript
let dish = React.createElement("h1",null,"baked salmon")

ReactDOM.render(dish,document.getElementById('react-container'))
```
제목 엘리먼트를 DOM으로 렌더링하면 HTML에 정의해둔 react-container라는 id를 가진 div의 자식으로 h1 엘리먼트가 추가된다.
```html
<body>
  <div id="react-container">
    <h1>baked salmon</h1>
  </div>
</body>
```

네이티브 애플리케이션을 만들 때에도 리액트를 사용할 수 있으므로(React Native), DOM 렌더링 기능은 ReactDOM으로 옮겨졌다. 

## 자식
ReactDOM에서는 한 엘리먼트만 DOM으로 렌더링 할 수 있다. 리액트는 렌더링할 엘리먼트에 data-reactroot이라는 태그를 단다. 다른 모든 리액트 엘리먼트는 이 루트 엘리먼트 아래에 내포된다.

리액트는 props.children을 이용해 자식 엘리먼트를 렌더링한다. 
위의 예제에서는 텍스트가 유일한 자식 엘리먼트였으므로 저렇게 쓰였으며, 텍스트가 아닌 리액트 엘리먼트를 자식으로 렌더링 할 수 있다.

```html
<ul class="ingredients">
  <li>연어 500 그램</li>
  <li>잣 1컵</li>
  <li>버터 상추 2컵</li>
</ul>
```

이는 리액트 엘리먼트로 다음과 같이 표현할 수 있다.
```javascript
React.createElement(
  "ul",
  null,
  React.createElement("li",null,"연어 500 그램")
  React.createElement("li",null,"잣 1컵")
  React.createElement("li",null,"버터 상추 2컵")
)
```