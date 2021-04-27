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
    <script src="https://unpkg.com/react@16/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
    <script>
      //순수 리액트 코드
    </script>
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