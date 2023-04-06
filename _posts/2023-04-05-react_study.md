---
layout : single
title : "react) javaScript - 수정중"
categories : React
tag : [React, React_Personal, Study, Udemy_STUDY, React_STUDY, javaScript]
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


수정중
