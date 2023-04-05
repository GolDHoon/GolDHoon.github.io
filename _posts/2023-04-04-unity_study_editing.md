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
# 유니티 3D 장애물 피하기 - 수정중

****유데미 강좌** : [https://www.udemy.com/course/best-3d-c-unity/](https://www.udemy.com/course/best-3d-c-unity/ "유데미 강좌 링크")**

**게임 디자인**

- 플레이어 : 움직일 수 있어야한다.
- 카메라 :  플레이어를 따라다닌다
- 장애물 : 플레이어가 피해야할 대상 (접촉 시 점수 삭감, 접촉시 표시, 장애물끼리 상호작용)
- 도착지점 : 플레이어가 도착하면 도착 안내 알림 출력
- 경사로 : 장애물이 중력의 영향을 받아 움직임 부여

**게임 디자인 시 중요 포인트**

- 플레이어의 관점에서 경험 고려
- 핵심 메카니즘
- 게임 루프 : 플레이어 클리어 포인트

---

**3D C# 기본구조**

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

**오브젝트 이동 스크립트**

```c#
public class ClassName : MonoBehaviour
{//필드맴버
	float xValue = 0f;
	[SerializeField] float yValue = 0.02f;
	float zValue = 0f;
}
```

[SerializeField] : Inspector에 값 표시

- 주의점 : Inspector의 값이 변경되어도 스크립트의 기존값이 변경되지는 않는다.

```c#
void Start()
{

}
```

```c#
void Update()
{
	transform.Translate(xValue, yValue, zValue);
}
```

transform : 게임의 오브젝트에 transform에 접근한다는 뜻

transform.Translate() : transform에 접근 하여 Translate라는 method를 불러온다는 뜻

---

**Material**

- 오브젝트의 색상 및 빛반사 등 설정
- 생성방법 : assets에서 마우스 우 클릭 -> Create -> Material
- 적용방법 : 생성된 asset을 객체에 드래그
