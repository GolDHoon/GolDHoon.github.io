---
layout : single
title : "sonarQube Blocker 결함 건"
categories : NewUcube
tag : [JAVA, sonarQube, NewUcube_sonarQube]
toc : true
toc_sticky : true
toc_label : 목차
author_profile : false
sidebar:
  nav : "docs_personal_corporate"
search: true
---
# 현상

`LocalDateTime` 객체에 `withHour` 등의 일시 지정 함수에서 `Use dicimal values instead of octal ones` Blocker 심각도 발생

---

# 원인

```java
//예시코드
public void function(){
    LocalDateTime now = LocalDateTime.now();
  
    now.withHour(00);
}
```

위 코드에서 `now.withHour(00);` 이 코드가 문제가 되는 것인데.... 왜?? int형 데이터에서 00이나 0이나 같은거 아닌가??

---

# 해소

```java
//예시코드
public void function(){
    LocalDateTime now = LocalDateTime.now();
  
    now.withHour(0);
}

```

일단 소스를 위처럼 고치니 `Use dicimal values instead of octal ones`의 심각도는 해소되었는데 원인을 모르겠다...
