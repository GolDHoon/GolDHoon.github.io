---
layout : single
title : "java 함수형인터페이스, 람다식"
categories : Java
tag : [JAVA, NewUcube_skil]
toc : true
toc_sticky : true
toc_label : 목차
author_profile : false
sidebar:
  nav : "docs_corporate_project"
search: true
---
# 개념

**함수형 인터페이스**

함수를 객체처럼 다룰수 있게 해주는 인터페이스. 호출하는 곳에서 로직을 구현하여 쓸 수 있게 해준다. 자바에서 기본적으로 제공되는 것이 있다.

**람다식**

함수를 간단한 하나의 식으로 표현하는 것 이름이 필요없기 때문에 익명함수의 한 종류이다.

---

# 기본 활용

**함수형 인터페이스**

```java
// 예시코드
interface InterfaceName<T>{
    T ifTest();
}

class ClassName{
    public void function(){
        InterfaceName<String> interfaceName = new InterfaceName() {
            return "TestCode";
        };

        System.out.println(interfaceName.ifTest());
    }
}
```

위 소스코드 처럼 인터페이스에 추상메소드를 만들고 난 후 클래스에서 해당 인터페이스의 메소드를 불러와 쓰는 식으로 쓸 수 있다. `System.out.println(interfaceName.ifTest());`에서는 결국 `TestCode`라는 문자열이 출력된다.

**람다식**

```java
// 예시코드
interface InterfaceName<T>{
    T ifTest();
}

public void function(){
    InterfaceName<String> interfaceName = () -> "TestCode";

    System.out.println(interfaceName.ifTest());
}
```

함수형 인터페이스의 소스코드를 위의 소스코드처럼 함축하여 쓸 수 있다.

---

# 람다식 규칙

함수명과 반환타입은 인터페이스에 이미 명시가 되어 있기 때문에 작성하지 않는다.

매개변수의 타입이 명시되어 있는 경우 생성자 부분에 타입은 생략가능하다.

- 매개변수가 2개 이상일 때는 생성자 부분에 타입 생략 불가

매개변수가 1개일 때 매개변수의 `()` 소괄호를 생략할 수 있다.

- 단 매개변수의 타입을 선언한 경우 불가능

body의  `{}` 중괄호를 생략 할수 있다.

- 단 복수의 line의 소스인 경우 불가

---

# JAVA에서 기본적으로 제공하는 함수형 인터페이스

| Interface Name       | Input Type                       | Return Type     | Method                    |
| -------------------- | -------------------------------- | ---------------- | ------------------------- |
| Predicate\<T>        | T(Generic Type)                  | boolean          | test(T t)                 |
| Consumer\<T>         | T(Generic Type)                  | void             | accept(T t)               |
| Supplier\<T>         | N/A                              | T(Generic Type)  | T get()                   |
| Function\<T, R>      | T(Generic Type)                  | R(Generic Type)  | R apply(T t)              |
| Comparator\<T>       | T(Generic Type)                  | int              | int compare(T o1, To2)    |
| Runnable             | N/A                              | void             | run())                    |
| Callable\<V>         | N/A                              | V(Generic Value) | v call() throws Exception |
| BiPredicate\<T, U>   | T(Generic Type), U(Generic Type) |                  | test(T t, U u)            |
| BiConsumer\<T, U>    | T(Generic Type), U(Generic Type) |                  | accept(T t, U u)          |
| BiFunction\<T, U, R> | T(Generic Type), U(Generic Type) | R(Generic Type)  | R apply(T t, U u)         |
