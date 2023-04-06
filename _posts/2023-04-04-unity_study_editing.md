---
layout : single
title : "unity) 3D 게임개발 - 장애물피하기 - 수정중"
categories : Unity
tag : [Unity, Unity_Personal, Study, Udemy_STUDY, Unity3D_STUDY]
toc : true
toc_sticky : true
toc_label : 목차
author_profile : false
sidebar:
  nav : "docs_personal_project"
search: true
---
**유데미 강좌** : [https://www.udemy.com/course/best-3d-c-unity/](https://www.udemy.com/course/best-3d-c-unity/ "유데미 강좌 링크")

# 게임 디자인

## 게임 디자인 시 중요 포인트

- 플레이어의 관점에서 경험 고려

- 핵심 메카니즘

- 게임 루프 : 플레이어 클리어 포인트

## 현 과제의 게임 디자인

**플레이어** : 움직일 수 있어야한다.

**카메라** :  플레이어를 따라다닌다

**장애물** : 플레이어가 피해야할 대상 (접촉 시 점수 삭감, 접촉시 표시, 장애물끼리 상호작용)

**도착지점** : 플레이어가 도착하면 도착 안내 알림 출력

**경사로** : 장애물이 중력의 영향을 받아 움직임 부여

---

# C# 코드

## 3D C# 기본구조

```c#
using System.Collections;
using System.Collections.Generic;
usgin UnityEngine;

public class ClassName : MonoBehaviour
{
	int var1 = 0; // 변수(기본형 데이터 종류 : int, float, bool, string 등)

    void Start()
	{	//스크립트가 호출되면 동작하는 스크립트

    }

    void Update()
	{	//스크립트가 실행되는 동안 지속적으로 동작하는 스크립트(해당 메소드 안의 모든 소스는 한 프레임 안에 실행된다.)

    }
}

```

## 오브젝트 이동 스크립트

```c#
public class Mover : MonoBehaviour
{//필드맴버
	float xValue = 0f;
	[SerializeField] float yValue = 0.02f;
	float zValue = 0f;

	void Start()
	{

	}

	void Update()
	{
		transform.Translate(xValue, yValue, zValue);
	}
}
```

[SerializeField] : Inspector에 값 표시

- 주의점 : Inspector의 값이 변경되어도 스크립트의 기존값이 변경되지는 않는다.

transform : 게임의 오브젝트에 transform에 접근한다는 뜻

transform.Translate() : transform에 접근 하여 Translate라는 method를 불러온다는 뜻

## 키보드 작동에 따른 오브젝트 이동 스크립트

```c#
public class Mover : MonoBehaviour
{
	void Start()
	{

	}

	void Update()
	{
		float xValue = Input.GetAxis({"Horizontal"});
		float zValue = Input.GetAxis({"Vertical"});
		transform.Translate(xValue , 0, zValue);
   	}
}
```

**Input.GetAxis** : Input manager에 속해있는 특정 축의 입력값을 가져오는 method

- 1(좌, 후, 하) 이나 1(우, 전, 상)의 출력값

**Input System**
플레이어로부터 전달 받을 수 있는 정보관리 system

접근 경로 : [Edit] - [Project Settings] - [InputManeger]

- 축 이동 설정 가능

**문제점**

- frame rate 현상 : 각 기기의 사양에 따라 FPS(Frame Per Second)가 전부 다르다. 위 소스코드 상으로는 update함수 안에서 이동시스템을 구현했는데, 이는 1프레임 당 실시되는 소스이기 때문에 이동시스템은 각 기기의 사양에 영향을 받게 된다.

```c#
public class Mover : MonoBehaviour
{
	void Start()
	{

	}

	void Update()
	{
		float xValue = Input.GetAxis({"Horizontal"}) * Time.deltaTime;
		float zValue = Input.GetAxis({"Vertical"}) * Time.deltaTime;
		transform.Translate(xValue , 0, zValue);
   	}
}
```

**개선사항**

- Time.deltaTime 적용
- Time.deltaTime : 프레임이 실행되는데 얼마나 걸렸는지 알수 있다.

속도 적용

```c#
public class Mover : MonoBehaviour
{
	[SerializeField] float moveSpeed = 10f; //이동속도

	void Start()
	{

	}

	void Update()
	{
		float xValue = Input.GetAxis({"Horizontal"}) * Time.deltaTime * moveSpeed;
		float zValue = Input.GetAxis({"Vertical"}) * Time.deltaTime * moveSpeed;
		transform.Translate(xValue , 0, zValue);
   	}
}
```

**현 과제에서 이동 시스템에서는 플레이어의 점프는 고려하지 않는다.**



---

# 3D 유니티 인터페이스

## Material

오브젝트의 색상 및 빛반사 등 설정

생성방법 : assets에서 마우스 우 클릭 -> Create -> Material

적용방법 : 생성된 asset을 객체에 드래그

## Cinemachine으로 카메라가 플레이어를 따라가게 하기

**특징** : scene에 있는 여러 카메라를 관리하고 쉽게 카메라의 rule을 추가할 수 있다.

**개념** : Cinemachine Brain을 추가하여 우리가 어떤 virtual 카메라를 봐야할 지 알도록 한다.

**Cinemachine package 설치 법**

1. [windows] - [package manager] - [Package: in Project] - [Unity Registry] - [Cinemachine 검색] - [install]
2. 설치가 완료 되면  Project의 Pakages에 Cinemachine이 추가된다.

**적용법**

1. Cinemachine Brain Component 추가
2. Hierachy의 main camera 클릭 후 Inspector의 add component에서 cinemachine을 검색하면 카메라에 추가할 수 있는 모든 cinemachine component가 나온다.
3. 상단 도구에서 [Cinemachine] - [Create virtual Camera]를 클릭
4. 생성된 sample scene를 클릭 후 카메라의 초점을 맞춰 준다.
5. 생성된 sample scene의 Inspector에서 [Body]의 종류를 Framing Transposer로 변경
   1. Follow 옵션 : 카메라 이동, 시점 고정
   2. Look at 옵션 : 카메라 고정, 시점 이동
   3. Camera Distance : 카메라와 object간의 거리
   4. play mode에서 수정한 설정 값들을 유지하고 싶으면 [Save During Play] 활성화
5. 설정이 완료 되었다면 생성된 sample scene 선택 해제

## 기본 충돌(Collision)

**적용방법**

1. Hierachy에서 플레이어 오브젝트를 클릭
2. Inspector에서 Add Component에서 Rigidbody 추가
3. rigidbody 속성 변경
   1. Use Gravity : 중력 사용여부 설정
   2. Constraints 설정 : Position(위치)와 Rotation(회전)을 알맞게 고정
