---
layout : single
title : "react) javaScript와 NEXT JS - 수정중"
categories : React
tag : [React, React_Personal, Study, Udemy_STUDY, React_STUDY, javaScript, NEXTjs]
toc : true
toc_sticky : true
toc_label : 목차
author_profile : false
sidebar:
  nav : "docs_personal_project"
search: true
---
**유데미 강좌** : [https://www.udemy.com/course/best-react/](https://www.udemy.com/course/best-react/ "유데미 강좌 링크")

**javaScript 자료** : [https://developer.mozilla.org/en-US/](https://developer.mozilla.org/en-US/ "mdn 링크")

# 변수

**let**  변수
**const** : 상수

---

# arrow 함수

**장점**

- 기존 함수에서 this를 사용하면 의도한 객체를 참조하지 않는 현상이 있는데 arrow 함수를 사용하면 항상 정의한 객체를 나타내고, 실행중에 갑자기 바뀌지 않는다.

**표현방법**

```javascript
//매개변수가 없을 때
function myFx(){
	console.log('Test');
}

const myFx = () => {
	console.log('Test');
}

myFx();
```

```javascript
//매개변수가 1개 있을 때
function myFx(var){
	console.log(var);
}

const myFx = var => {
	console.log(var);
}

myFx('Test');
```

```javascript
//매개변수가 2개 이상 있을 때
function myFx(var1, var2){
	console.log(var1, var2);
}

const myFx = (var1, var2) => {
	console.log(var1, var2);
}

myFx('Test', 1)
```

- 매개변수가 1개일 때만 매개변수 선언부 소괄호 생략가능

```javascript
//리턴 값 표현
function myFx(var){
	return console.log(var * 2);
}

const myFx = (var) => console.log(var * 2);

console.log(myFx(2));
```

```javascript
//내부 로직이 있을 때 body return 표현
function myFx(var){
	let value = var * 2;
	return console.log(value);
}

const myFx = (var) => {
	let value = var * 2;
	return console.log(value);

console.log(myFx(2));

```

- 함수의 body 부분이 1 Line뿐인 경우 body를 감싸는 중괄호 생략 가능

---

# Exports & Imports

**표현방법**

```javascript
//파일명 jsExam1.js
const valueJson = {
	key1 = 'value1'
};

export default valueJson;
```

- default 키워드는 파일에서 어떤 것을 가져오면 항상 export가 내보낸 것을 기본값으로 가져온다는 의미(항상 참조한다는 의미)

```javascript
//파일명 jsExam2.js
export const utils = () => {...};
export const data = 10;
```

- default 키워드가 없기 때문에 정확한 키워드를 중괄호 안에 표시 해야한다.

```javascript
//파일명 app.js
import valueJson from './jsExam1.js';
import value from './jsExam1.js';

import {data} from './jsExam2.js';
import {util as utils} from './jsExam2.js';
import {data, utils} from './jsExam2.js';
import * as bundled from './jsExam2.js';
```

- as 키워드는 자유롭게 스크립트의 별칭을 설정 가능 (alias)

* \* 키워드는 javaScript파일의 모든 스크립트를 불러올 수 있다. `bundled.date` 와 같이 호출할 수 있다.

- NEXT JS의 모든 기능들이 모든 브라우저에서 작동하지 않는다. NEXT JS를 현재 브라우저에서 지원가능한 javaScript 기능으로 컴파일필요.

---

# classes

**javaScript의 객체**

* **표현방법**

```javascript

class ClassName{
	//property
	key1 = 'value1';
	//method
	fx = () => {...};
}

//class 사용방법
const obj1 = new ClassName();
obj1.fx();
console.log(key1);
```

**class의 상속**

```javascript
class Class2{
	key1 = 'value1';

	printKey1 = () => console.log(key1);
}

class Class1 extends Class2{
	key2 = 'value2';

	printKey2 = () => console.log(this.key2);
}

const fx = new Class2();
fx.printKey1();
fx.printKey2();
```

- javaScript 버전 ES7이 업그레이드 되면서 `super()` method와 `this`의 생략이 가능해졌다.

---

# spread와 rest operators

**spread 연산자 [`...`]** : 배열 및 객체의 property 전체 추가

```javascript
const oldArray = [1, 2];
const newArray = [...oldArray, 3, 4];
const oldObject = {oldProp : 5};
const newObject = {...oldObject, newProp:6};
```

**rest 연산자 [`...`] **: 함수의 인수 목록을 배열로 합치는데 사용

```javascript
function sortArgs(... args){
	return args sort();
}
```

---

# Destructuring(구조분할)

**역할** : 배열의 원소나 객체의 property를 추출해서 변수에 저장할 수 있도록 한다.
**spread와 차이점**

- spread : 모든 원소와 property를 가져와서 새 배열이나 객체등에 전달
- destructuring : 원소나 property 하나만 가져와서 변수에 저장
- Array Destructuring

```javascript
[a, b] = ['Hello', 'ESC'];
console.log(a); //Hello
console.log(b); //ESC
```

- Object Destructuring

```javascript
{name} = {name : 'Hoon', age:32}
console.log(name); //Hoon
console.log(age); //undefined
```

---

# 참조형 및 기본형 데이터타입

**기본형 데이터 타입** : number, string, boolean 등//기본형을 참조하는 경우

```javascript
let num1 = 1;
const num2 = num1;

console.log(num2);//1
num1 = 2;
console.log(num2);//1
```

- 기본형 데이터를 참조하는 경우 값을 복사

```javascript
//참조형을 참조하는 경우
const person = {
	name : 'hoon'
}

const person2 = person;

console.log(person2);
/* 출력값
[object Object] {
  name: "hoon"
}
*/
person.name = 'Gol.D.Hoon';
console.log(person2);
/* 출력값
[object Object] {
  name: "Gol.D.Hoon"
}
*/
```

- 참조형 데이터를 복사하는 경우 객체는 메모리에 저장되어 있고 상수는 메모리에 있는 주소값을 저장

---

# 배열 함수의 새로고침

```javascript
const numbers = [1, 2, 3];

const doubleNumArray = numbers.map((num) => num * 2;);
```

- `.map()` : javaScript 내장 배열함수
