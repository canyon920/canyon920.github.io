---
title: Javascript 데이터 구조 
tags:  stack, que
---
 

기본 자료형 : 숫자, 문자열, 불  => Stack 
복합 자료형: 배열, 함수, 객체 => Heap 

변수와 상수를 만든 다는 것은
Stack 에 있는 상자에 이름을 넣어주는 것 

a = 10 

a = 10  => a라는 이름을 붙인 것
b = "안녕" > b라는 이름을 붙인 것 

배열은 굉장히 커서 Stack 에 넣을 수 없음


c = [1,2,3]
배열을 만들게 되면 Heap 에 배열이 생성되고, 1,2,3 이라는 배열이 만들어짐  

console.log(c) => 메모리 스택에 쌓여있는 이름을 참조하는 것 


메모리 스택에 쌓아놓은  C 


주소는 어떠한 데이터가 있는 위치를 나타냄.

스택: 기본 자료형과 주소 등을 저장하는 메모리 공간
힙 : 복합 자료형을 저장하는 메모리 공간 
주소: 저장된 자료의 위치 
레퍼런스한다: 스택의 주소가 힙의 자료를 가리키는 것 
레퍼런스 변수: 스택에 저장된 것중에 저장소가 저장된 변수 


비파괴적 처리와 파괴적 처리 
let a = 10 
let b = 20 
a + b  = 30 
이라는 값이 나옴 

a = 10 

b = 20 

let c = [1,2,3]

c.push(4)

어떠한 처리후 원본이 변경되지 않는다 => 비파괴적 처리
어떠한 처리 후 원본이 변경된다 => 파괴적 처리 

+ 연산은 비파괴적으로 처리를 하고, 배열에 대한 push 연산은 파괴적으로 처라히는지에 대해 

스택에 데이터 흐름은 굉장히 단순하게 흘러가지만, 힙의 경우 데이터 흐름이 단순하지 않ㅇ므 


스택은 단순하게 데이터 구조가 흐르기 때문에 영향을 주지 않지만, 힙의 경우 데이터 구조가 복잡하기 ㅇ흐르기 때문에 
데이터를 처리하는 속도에 영향을 줌 


psuh() 메서드가 비파괴적으로 행동한다면 원본도 그대로 냅두고, 새로운 배열을 만들고 이 위치를 다른 변수에 저장해서 활용을 하게 될 것인데 Javascript 는 1995년 경에 만들어졌기 때문에, 컴퓨터 메모리가 굉장히 부족했기 때문에, 이러한 데이터를 복제해서 사용하는 것이 컴퓨터에게 굉장히 부담스러웠기 때문에,  복제 해서 사용하는 것을 포기하고, 기존 배열에 값을 직접적으로 수정하는 방법을 채택했고
c.push() 하게 되면, c안에 있는 메모리 스택에 영향을 주게 됩니다.

비파괴적 처리를 현대에서는 더 많이 하는데, 2010년 이후에 추가된 메서드들은 비파괴적 처리를 하게 됩니다.
함수의 메서드들만 보고는 이 데이터들이 동적으로 파괴되는지, 안되는지 알 수 없습니다.

const b = [1, 2]
b.push(3)

const 는 stack 에 있는 값을 변경하지 못하게 하는 것


const 스택 X

const 스택 10 => 20 // 오류 


const 가 박혀있어도 배열 관련된 것들은 처리가 가능하다는 것 

# 스택과 힙 

저장을 할 때 사용하느 ㄴ공간
- 스택(stack) : 스택을 쌓는 공간[잘 쌓는 공간]
 -> 기본 자료형은 직접!
 -> 복합 자료형은 그 주소(Address)!

- 힙(heap) : 힙힙 던져서 쌓는 공간[대충 큰 것들을 던져서 쌓은 공간] 
 -> 복합 자료형의 본체가 저장!

#파괴와 처리 and 비파괴적 처리
처리 후에 
- 원본이 변경되었다 -> 파괴적 처리 
- 원본이 변경되지 않았다 -> 비파괴적 처리 

const 의 제한 
const -> 스택에 있는 값 변경할 때 오류!!! 
-> 힙에 있는 레퍼런스된 복합 자료형을 조작하는 것에는 문제 X 


---

React.html :star2:

[![Star This Project](https://img.shields.io/github/stars/kitian616/jekyll-TeXt-theme.svg?label=Stars&style=social)](https://github.com/canyon920/)