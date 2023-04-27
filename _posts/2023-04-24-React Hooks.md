---
title: LifeCycle Hook
tags: React, Functional Hook 
---

최근에 React 18버전으로 업데이트하면서 굉장히 많은 Hook 들이 생겨났습니다.


useState() 
사용자 입력과 같은 정보를 기억할 수 있습니다.
예를 들어 양식 구성 요소는 상태를 사용하여 입력 값을 저장할 수 있는 반면, 이미지와 갤러리 구성 요소는 상태를 사용하여 선택한 이미지 인덱스를 저장할 수 있습니다.


useReducer() 
리듀서 함수 내부에 업데이트 로직이 있는 상태 변수를 선언 합니다.
useReducer 는 두개의 값을 가진 배열을 반환 합니다.
상태를 다른 값으로 업데이트하고 렌더링을 트리거할 수 있는 기능은 dispatch 입니다.




```js
import { useReducer } from 'react';
function reducer(state, action){
  // ...
}

// React의 Reducer는 현재와 함께 제공한 함수 state 와 전달한 작업을 호출한 결과로 다음 상태를 전달합니다. dispatch

```

매개변수는 action => 사용자가 수행한 작업입니다. 모든 유형의 값이 될 수 있습니다.
일반적으로 작업을 식별할 속서오가 선택적으로 추가 정보가 있는 다른 속성이 있는 개체 입니다.

dispatch 


contextHooks 
컨텍스트를 사용하면 구성 요소가 소품으로 전달하지 않고 멀리 떨어진 부모로부터 정보를 받을 수 있습니다.
예를 들어 앱의 최상위 구성 요소는 깊이에 관계 없이 현재 UI 테마를 아래의 모든 구성 요소에 전달할 수 있습니다.




useContext ()  
구성 요소의 최상위 수준에서 호출하여 컨텍스트를 읽고 구독합니다.

useContext 전달한 컥텍스트에 대한 Context Value를 반환 합니다. 
컨텍스트 값을 결정하기 위해 React는 구성 요소 트리를 검색하고 해당 특정 컨텍스트에 대해 가장 위에서 가장 가까운 Context의 Provider 를 찾습니다.

Context에 전달하려면 Button 해당 Context 의 공급자로 Context 또는 상위 구성 요소 중 하나를 감쌉니다.

항상 호출하는 구성 요소 위에서 가장 가까운 공급자를 찾습니다. 위쪽으록 검색하고 호출하는 구성 요소의 공급자를 고려하지 않습니다.


```js 
function MyPage(){
  return (
    <ThemeContext.provider value="dark">
      <Form />
    </ThemeContext.Provider>
  )
}
function Form() {
    return (
        <Panel title="Welcome">
          <Button> Sign up </Button>
          <Button> Log in </Button>
        </Panel>
    );
}

function Panel({title, children}){
    const theme = useContext(ThemeContext);
    const className = 'panel-' + theme;
    return (
        <section className={className}>
            <h1> [title] </h1>
              {children}
        </section>
    )
}

function Button({children}){
    const theme = useContext(ThemeContext);
    const className = 'button-' + theme';
    return (
      <button className={className}>
        {children}
      </button>
    )
}
```

Ref Hooks 


EffectHooks 

Performance Hooks 


# Other Hoosk 

useDebug Value 

useId 

useSyncExternalStore

 
```



```




---

React-Hook.html :star2:

[![Star This Project](https://img.shields.io/github/stars/kitian616/jekyll-TeXt-theme.svg?label=Stars&style=social)](https://github.com/canyon920/)