---
title: Javascript && TypeScript
tags:  Javascript, TypeScript, anyScript
---
   

ING ...
Javascript 의 Super Set 언어 


Javascript => 덕 타이핑
TypeScript => 고차적 언어 

typeSscript Type === typeof 결괏값


정적 언어로 코드를 실행하지 않고 어떤 오류를 안고 있는지 확인 가능 


정적 타입 검사 
정적 타입 시스템: 우리가 작성한 프로그램에서 사용된 값들의 형태와 동작을 설명 
TypeScript 와 같은 타입 검사기는 이 정보를 활용하여 프로그램이 제대로 작동하지 않을 때 우리에게 알려줍니다.

```js
const message = "Hello";



message() 
=> 
This expression is not callable.
  Type 'String' has no call signatures.
```



```js
const User = {
    name: "Daniel",
    age: 26,
}
user.location; 
 ```

Javascript 는 호출이 가능하지 않는 것에 대해 호출을 시도할 경우 오류가 발생 
객체에 존재하지 않는 프로퍼티에 접근을 시도 => 오류가 발생해야 됨 

```js
하지만 Javascript 는 undefined 를 반환 
const user = {
    name: "dongwon",
    age: 32
}


user.location; // undefined 
```

정적 타입 시스템은 어떤 코드가 오류를 발생시키지 않는 "유효한" Javascript 코드 일지라도, 
정적 타입 시스템 내에서 오류로 간주되는 경우라면 이를 알려주어야 합니다.

TypeScript에서는, 아래의 코드는 location 이 정의되지 않았다는 오류를 발생 시킵니다.


아래와 같이 오타가 발생할 경우 TypeScript 는 바로 잡아낼 수 있습니다.
( 빨간 줄이 표시됩니다. )


```ts 
const announcement = "Hello World";

announcement.toLocaleLowerCase()
announcement.toLocalLowerCase()


```



호출되지 않은 함수의 예제 입니다.
```js 
function fliCoin(){
    return Math.random < 0.5
// Operator '<' cannot be applied to types '() => number' and 'number'.

}
```


또는 기본적인 논리 오류 등이 있습니다.
하하.. 뒤에 꼭 시용되는 값을 넣어야 하는 거였군요...(?)

```ts 
const value = Math.random() < 0.5 ? "a" : "b";
if (value !== "a"){
  // ...
} else if ( value === "b"){
  // This comparison appears to be unintentional because the types '"a" and '"b"' have no overlap.  } 
}
```


프로그래밍 도구로서의 타입 

우리가 실수를 저지르는 바로 그 순간 바로 버그를 발견합니다.

타입 검사기는 우리가 변수 또는 다른 프로퍼티 상의 올바른 프로퍼티에 접근하고 있는지 여부를 검사할 수 있도록 
관련 정보들을 가지고 있습니다. 이 정보를 활용하면 타입 검사기는 우리가 사용할 수 있는 프로퍼티를 제안할 수 있게 됩니다.

즉 TypeScript 는 코드 수정에 활용될 수 있고, 우리가 코드를 입력할 때 오류 메시지를 제공하거나 코드 완성 기능을 
제공할 수 있습니다. 이는 TypeScript 에서 도구(Tooling)을 논할 때에 흔히 언급되는 내용 입니다.


TypeScript 를 지원하는 코드 편집기는 오류를 자동으로 고쳐주는 "Quick Fixes", 코드를 간편하게 재조직하는 리펙토링, 변수의
정의로 빠르게 이동하는 유용한 네비게이션, 주어진 변수에 대한 모든 참조 검색등의 기능을 제공 

이 모든 기능들은 타입검사기를 기반으로 하며 완전히 크로스 플랫폼으로 동작 



```ts
function greet(person, data){
    console.log(`Hello ${person}, today is ${data})
}

greet("Brendand")
```

tsc hello.ts 를 다시 실행하면, 커맨드 라인 상에서 오류를 얻게 됨 
Expected 2 arguments, but got 1 



오류 발생 시키기
코드에 대한 타입 검사는 프로그램이 실행할 수 있는 동작을 제한 합니다.
따라서 타입 검사가 허용 또는 제한하는 동작의 범위에는 어느 정도 절충과 타협이 존재 합니다.
대부분의 경우 문제가 발생하지 않지만, 타입 검사가 방해가 되는 시나리오 또한 존재 합니다.
예를 들어 Javascript로 작성된 코드를 TypeScript 로 마이그레이션 하는 과정에서 타입 검사 오류가 발생하는 경우를
떠올려 보세요. 결국에는 타입 검사를 통과하도록 코드를 수정해나가겠지만, 사실 원본 Javascript 코드는 이미 제대로 잘 작동하고 있는 상태 였습니다. Typescript 로 변환하는 작업 때문에 코드 실행이 중단되어야 할 이유가 있을까요?



컴파일러 옵션

--noEmitOnError  .
TypeScript 는 당신을 방해하지 않습니다. 물론, 시간이 흐름에 따라 좀 더 실수에 방어적으로 대응하고, 
TypeScript 가 보다 엄격하게 동작하기를 원할 수도 있습니다.
```ts
tsc --noEmitOnError 파일명.ts

```


명시적 타입 

```ts
function greet(person: string, date: Date){
    console.log(`Hello ${person}, today is ${date.toDateString()}!`);
}
```

방금 우리는 person 과 date 에 대하여 타입 표기를 수행하여 greet 가 호출될 때 함께 사용될 수 있는 값들의 
타입을 설명했습니다. 해당 시그니처는 "greet 는 string 타입의 person 과 Date 타입의 datae를 가진다"고 해석할 수 있습니다.

이것이 있다면 TypeScript 는 우리가 해당 함수를 올바르지 못하게 사용했을 경우 이를 알려줄 수 있게 됩니다.

```ts
let msg = "hello there";
```

``` ts
// TypeScript Offical 

msg 가 string 타입을 가진다는 사실을 Typescript 에게 알려주지 않았더라도 
TypeScript 는 이를 알아낼 수 있습니다. 본 기능이며, 타입 시스템이 알아서 올바른 타입을 어떻게든 잘 알아낼 수 있다면
타입 표기를 굳이 적지 않는 것이 가장 좋습니다.

// 참고 바로 위 코드의 말풍성은 에디터에서 해당 코드를 작성 했을 때, 해당 변수에 마우스 호버시 화면에 타나나는 내용 입니다.
```


지워진 타입 
1. Person 과 date 인자는 더 이상 타입 표기를 가지지 않습니다.
2. "템플릿 문자열" - 백틱(` 문자)을 사용하여 작성된 문장 - 은 연결 연산자(+) 로 이루어진 일반 문자열로 변환 되었습니다.


두번째 항목에 대하여서는 이후 자세히 다루도록 하고 우선 첫번째 항목에 초점을 두도록 하겠습니다.
타입 표기는 Javascript(또는 엄밀히 말하여 ECMAScript)의 일부가 아니므로, Typescript 를 수정 없이 그대로 실행할 수 있는 
브라우저나 런타임은 현재 존재하지 않습니다. 이것이 TypeScript 를 사용하고자 할 때 다른 무엇보다도 컴파일러가 필요한 이유 입니다.
TypeScript 전용 코드를 제거하거나 변환하여 실행할 수 있도록 만들 방법이 필요 합니다. 대부분의 TypeScript 전용 코드는 제거되며, 마찬가지로 타입 표기 또한 완전히 지워 집니다. 


!! 타입 표기는 프로그램의 런타임 동작을 전혀 수행하지 않습니다
gg


다운 레벨링 
앞서 언급된 또 다른 차이점은, 바로 템플릿 문자열이 아래의 내용에서

```ts
`Hello ${person}, today is ${date.toDateString()}!`};
은 아래의 내용으로 다시 작성되었다는 점 입니다.

"Hello" + person + ", today is" + date.toDateString() + "!";

```




React.html :star2:

[![Star This Project](https://img.shields.io/github/stars/kitian616/jekyll-TeXt-theme.svg?label=Stars&style=social)](https://github.com/canyon920/)