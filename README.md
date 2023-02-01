# react_basic_nomad

Nomad - ReactJS로 영화 웹 서비스 만들기

## 2.0 Introduction

- React 는 UI를 interactive(상호작용) 하게 만들어 준다.
- vanilla JS 와 React JS 비교할 예정

## 2.1 Before React

- vanilla JS로 버튼 만들기

```js
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Document</title>
  </head>
  <body>
    <span>Total Clicks : 0</span>
    <button id="btn">Click me</button>
  </body>
  <script>
    let counter = 0;
    const button = document.getElementById("btn");
    const span = document.querySelector("span");
    function handleClick() {
      console.log("i have been clicked");
      counter += 1;
      span.innerText = `Total Clicks : ${counter}`;
    }
    button.addEventListener("click", handleClick);
  </script>
</html>
```

- react 사용 세팅하기

```js
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Document</title>
  </head>
  <body></body>
  <script src="https://unpkg.com/react@17.0.2/umd/react.production.min.js"></script>
  <script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js"></script>
</html>
```

## 2.2 Our First React Element

- React Js : 어플리케이션을 interactive 하도록 만드는 library
- react-dom : package or library / React element를 HTML body에 둘 수 있도록 해주는 역할
  <br><br>
- ReactDOM.render() - render의 의미는 react element를 가지고 HTML로 만들어 배치한다는 것. 즉, 사용자에게 보여준다는 의미
  - ReactDOM.render(span, span이 가야할 위치)
  - 보통 body에 id=“root” 만들어서 span을 root 안에 두라고 함
- React.createElement("span", {span의 property}, “span의 내용”)
  <br><br>
- 바닐라JS는 HTML -> JS 순서
- 리액트는 JS -> HTML 순서
  <br><br>
- JS가 element를 생성하고 React JS가 그것을 HTML로 번역하는 것
- React JS는 업데이트 해야 하는 HTML을 업데이트 할 수 있음

## 2.3 Events in React

- h3, btn 두 가지를 render 하고 싶은 경우

  - const container = React.createElement("div", null, [span, btn]);
  - 배열을 만들어서 넣어준다.

- property에 eventListener 넣는 것도 가능.
  - 클릭 {onClick: () => console.log("I'm clicked")}
  - 마우스엔터 {onMouseEnter: () => console.log("mouse enter")}

## 2.5 JSX

- JSX : js를 확장한 문법

  - JSX를 사용하려면, babel 필요

- 실습 : JSX형식으로 react 컴포넌트 만들기
