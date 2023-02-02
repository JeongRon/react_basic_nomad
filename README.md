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

## 2.6 JSX part Two

- 컴포넌트 만들기
  - Arrow function style
    - return X
    - const Button = () => (...)
  - fucniton sytle
    - return O
    - function Title() {... return();}

## 3.0 Understanding State

- 리렌더링
  - React는 바뀐 부분만 UI 업데이트
  - JS는 노드 정보가 바뀔때마다 노드트리를 모두 업데이트
- 현재 코드는 렌더링 함수를 만들어 업데이트 시 리렌더링 되게 구현

## 3.1 setState part One

## 3.2 setState part Two

- 리렌더링 하는 방법 - setState
  - const [counter, setCounter] = React.useState(0);

```js
 const root = document.getElementById("root");
    function App() {
      const [counter, setCounter] = React.useState(0);
      const onClick = () => {
        setCounter(counter + 1);
      };
      return (
        <div>
          <h3>Total clicks: {counter}</h3>
          <button onClick={onClick}>Click me</button>
        </div>
      );
    }
    ReactDOM.render(<App />, root);
  </script>
```

## 3.4 State Functions

- setState 로 현재 값을 바꾸기
  1. 직접 할당 : setCounter(state + 1);
  2. 함수를 할당 : setCounter((current) => current + 1);
  - 2번 함수를 할당하는 것이 더욱 안정성이 높다 함

## 3.5 Inputs and State

- JSX는 class / for 과 같이 JavaScript에서 선점된 문법 용어를 사용 못한다.
  - class는 className으로 for은 htmlFor로 바꿔쓴다
- controlled component
  - Input 태그 나오면 value, onChange 속성을 붙여서 상태를 관리

## 3.6 State Practice part One

- 분 입력시, 시간이 자동으로 업데이트 되게끔 설정하기
  - hours input 에도 value 속성 안에 상태 지정
- reset 버튼 만들기
  - button 태그의 onClick 속성 지정

## 3.7 State Practice part Two

- flip 구현하기
  - 분 입력일때, 시간은 disabled=true / 시간 입력일때, 분은 disabled=true
  - const [flipped, setFlipped] = React.useState(false);
- 시간 -> 분 컨버터 만들기
  - 삼항 연산자 사용
  - value={flipped ? amount : amount / 60}
  - value={flipped ? amount \* 60 : amount}

## 3.9 Final Practice and Recap

- 컴포넌트 나누기
- 컴포넌트를 select 할 수 있게 구현 하기
  - index state 사용

## 4.0 Props

- Props 사용하기
  - 비슷한 버튼을 만들기
  - text, font-size 만 props를 활용해서 넘겨주기

```js
function Btn({ banana, big }) {
  return (
    {banana}
    {big}
  );
}

function Btn(props) {
  return (
    {props.banana}
    {props.big}
  );
}
```

## 4.1 Memo

1. props에 function도 보낼 수 있음

- 이것은 JSX로 html 태그 자체에 이벤트 리스너를 넣는것과는 전혀 다른 것임.
- 그저 이벤트를 실행시키는 함수가 프로퍼티로 들어간 것임.

2. 불필요한 re-render는 React.memo()로 관리할 수 있음

- 부모 컴포넌트의 state를 변경하면 당연히 그 자식 컴포넌트들도 Re-render가 일어남.
- 불필요한 렌더링이 발생할 수도 있는데, 이 경우에는 React.memo()로 prop의 변경이 일어난 부분만 렌더링 시킬 수 있음.
- React.memo()
  - 컴포넌트가 React.memo()로 wrapping 될 때, React는 컴포넌트를 렌더링하고 결과를 메모이징(Memoizing)한다. 그리고 다음 렌더링이 일어날 때 props가 같다면, React는 메모이징(Memoizing)된 내용을 재사용한다.
