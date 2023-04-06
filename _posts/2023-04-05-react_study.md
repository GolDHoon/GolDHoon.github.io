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
# 변수

**let**  변수
**const** : 상수

---

**arrow 함수**

- 장점 : 기존 함수에서 this를 사용하면 의도한 객체를 참조하지 않는 현상이 있는데 arrow 함수를 사용하면 항상 정의한 객체를 나타내고, 실행중에 갑자기 바뀌지 않는다.

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

**Exports & Imports**

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

**classes**

- javaScript의 객체

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
consloe.log(key1);
```

- class의 상속

```javascript
class Class2{
	constructor(){
		this.key1 = 'value1';
	}
	printKey1(){
		console.log(this.key1);
	}
}

class Class1 extends Class2{
	constructor(){
		super();
		this.key2 = 'value2';
	}
	printKey2(){
		console.log(this.key2);
	}
}

const fx = new Class2();
fx.printKey1();
fx.printKey2();
```

- 상속받는 class에서는 반드시 생성자 함수 안에 `super()` method를 추가해야한다. `super()` : 상위 class의 생성자함수 실행

수정중
