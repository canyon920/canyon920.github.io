---
title: REACT
tags: React, Functional Hook 
---

REACT 의 18 버전에 대해 적어보고자 합니다. 

React 의 Functional Component 는 이런식으로 구현되어 있습니다.

```javascript
function ReactApp(){
  return(
    <button> Button </button>

  )
} 
```
이렇게 생성된 Component 를 다른 Component의 구성 요소에 중첩 할 수 있습니다.
```javascript 
export default function MyApp(){
  return (
    <div>
      <h1> Welcome to my app </h1>
      <ReactApp />
    </div>
  )
}


export default function App(){
  const [count, setCount] = useState(0);
  
  function handleClick(){
    setCount(count + 1);
  }
  return (
    <div>
      <h1> Counter the Update separetely </h1>
      <MyApp count={count} onClick={handleClick} />
      <MyApp count={count} onClick={handleClick} />
    </div>
  )
}

```
이렇게 데이터를 전달하는 정보를 Props 라고 합니다.
이제 상태와 이벤트 핸들러가 App 에 포함되어 있는 것을 알 수 있고, 두 가지 버튼에 대한 소품으로 count handleClick에서 count를 전달 합니다.

마지막으로 상위 구성 요소에서 전달한 소품을 읽고 MyApp 으로 변경 합니다.

```javascript
function MyApp({ count, onClick}){
  return (
    <button onClick={onClick}>
      Click {count} tiems 
    </button>
  )
}
```

버튼을 클릭하면 onClick 핸들러가 실행 됩니다. 각 버튼의 소품은 내부의 함수 onClick 으로 설정되었으므로, 내부의 코드가 실행 됩니다.
해당 코드를 호출하여 상태 변수를 증가 시킵니다. 새 값은 각 버튼에 소품으로 전달 되므로 모두 새 값을 표시 합니다.
이를 리프팅 상태 업 이라고 합니다ㅏ. 상태를 위로 이동하여 구성 요소 간에 공유 했습니다. 



---

Index.html :star2:

[![Star This Project](https://img.shields.io/github/stars/kitian616/jekyll-TeXt-theme.svg?label=Stars&style=social)](https://github.com/kitian616/jekyll-TeXt-theme/)
