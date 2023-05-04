---
title: REACT
tags: React, Functional Hook 
---

Components 에 대한 학습을 진행해 보도록 하겠습니다.

```js
function WebApp(){
  return (
    <div> Hello World </div>
  )
}
```

이러한 Component 에는 중첩 Component 구현이 가능합니다.

```js
function App(){
  return(
    <div>
      <h1> Welcome to my app </h1>
      <WebApp />
    </div>
  )
}

export default function WebApp(){
  return(
    <div>
      <h1> Welcome to my app </h1>
      <button> Button </button>
    </div>
  )
}
```

Conditional Rendering (조건부 렌더링)
조건을 작성하기 위한 특별한 구문이 없습니다. 대신 일반 Javascript 코드를 작성할 때 사용하는 것과 동일한 기술을 사용 합니다.

```js
let content;
if (isLoggedIn){
  content = <AdminPanel />;
} else {
  content = <LoginForm />;
}
return (
  <div>
    {content}
  </div>
)

// 위와 같은 문법은 JSX 문법을 이용하여 조금 더 간단하게 사용할 수 있습니다.

<div>
 {isLoggedIn ? ( <AdminPanel /> 
  ) : (
    <LoginForm />
)}
</div>
```

분기가 필요하지 않은 경우 더 짧은 논리 구문을 else 로 사용할 수도 있습니다.

```js
<div>
  {isLoggedIn && <AdminPanel />}
</div>
```

이러한 모든 접근 방식은 특성을 조건부로 지정하는 데에도 작동 합니다.



렌더링(Renderling) 목록 

```js
const products = [
  {title: 'Cute', yn: false,  id:1},
  {title: 'Cube', yn: false, id:2},
  {title: 'Move', yn: true, id:3},
]

const listItems = products.map(product) => 
  <li key={product.id}>
    {product.title}
  </li>

return (
  <ul> {listItems} </ul>
)

```

Key 값은 가져올 데이터의 고유 값으로 지정해야 합니다.


```js
const products = [
  {title: 'Cute', id:1},
  {title: 'Cube', id:2},
  {title: 'Move', id:3},
]

export default function App(){
  const listItems = products.map(product => 
    <li key={product.id}
        style={{color: product.yn ? 'black' : 'red'}}
        >
    {product.title}
  </li>

  return (
    <ul><listItems></ul>
  )

```

이벤트 응답 
구성 요소 내에서 Event Handler 함수를 선언하여 이벤트에 응답할 수 있습니다.

```js
function MyButton(){
  function handleClick(){
    alert('클릭')  
  }
  return (
    <button onClick={handleClick}> 클릭 </button>
  )
}
```

화면 업데이트 
구성 요소가 일부 정보를 기억하고 표기하기를 원할 때, useState 로 데이터 상태를 가져와야됩니다.

```js
import { useState } from 'react';
```

```js
function MyApp(){
  const [count, setCount] = useState(0);
}
```


```js
function MyApp(){
  const [count, setCount] = useState();

  hnadleClick = () => {
    setCount(count +1);
  }
  return (
    <button onClick={handleClick}>
    Clicked {count} times </button>
  )
}
```

useState 는 현재 상태의 count 와 이를 업데이트 할 수 있는 기능의 두가지를 할 수 있습니다.
버튼을 클릭할 경우 handleClick 이벤트가 발생하게 되고 setCount 에서는 count + 1을 증가시키는 Event가 발생 합니다.


Hooks 사용하기
함수가 시작중에 Hook을 요청하는 것을 의미 합니다.

useState 는 리액트에서 공급하는 Hook 중 하나이며, 그 외에도 많은 Hook 들이 존재 합니다.

위와 같은 방식은 공통된 부모의 Component 에서 중첩 구성요소로 중복되게 Component 를 구성한다고 똑같이 동작하지 않습니다.
아래와 같이 별개로 각 Component 에 기능을 부여해야지만, 각 Component 들이 똑같이 동작하게 됩니다.


handleClick 이벤트가 발생시에 setCount의 count를 1 발생시키는 이벤트인데요.


아래의 절차는 이것과 같습니다.


- 형이 퇴근하고 집에 들어 왔다.
- 눈에 먼저 보인 동생이 "형 나 과자 하나만" 하고 말한다.
- 형은 "응 알겠어 ~" 하고 나갔는데, 다른 동생이 방에서 "형 나도나도 !!" 하고 말한다 
- 형은 이미 과자를 사러 갔기 때문에, 다른 동생의 시킨 셔틀 행위는 하지 못했습니다.



```js
function App(){
  return (
    // ...
      <MyButton />
      <MyButton />
    // ...
  )
}

function MyButton(){
  const [count, setCount] = useState(0);
  const eventHadleing = () => {
    setCount(count+1)
  }
  return (
    <button onClick={eventHadleing}> 증가 </button>
  )
}
```



하지만 아래와 같다면 어떨까요?


- 형이 퇴근하고 집에 들어 왔다. 
- 동생 2명이 형한테 "나 간식사줘 배고파.." 하고 말했습니다.
- 형이 "응 알겠어~", 하고 간식을 2개 사들고 집에 올 수 있게 되겠죠?

를 코드로 풀어보도록 하겠습니다.


```js 
functino App(){
  const handleClcik = () => {
      //...
  }
  return (
    // ...
      <myApp button count={count} onClick={handleClick} />
      <myApp button count={count} onClick={handleClick} />
    // ...
  )
}


function MyButton({count, onClick}) {
  return (
    <button onClick={onClick}>
      간식 { count }
    </button>
  ) 
}

```


이렇게 전달하는 데이터를 props 라고 합니다.
이제 구성 요소에는 상태와 이벤트 핸들러가 App 포함되어 있으며, 이 두가지 모두를 각 버튼에 대한 소품으로 전달합니다.




---

React.html :star2:

[![Star This Project](https://img.shields.io/github/stars/kitian616/jekyll-TeXt-theme.svg?label=Stars&style=social)](https://github.com/canyon920/)