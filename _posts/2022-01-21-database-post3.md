---
layout: post
title:  "[데이터베이스] 데이터베이스개론 CH3 "
date:   2022-01-21
categories: database
---

# Chapter 3 데이터베이스 시스템

- 데이터베이스 시스템의 정의

	* 데이터베이스 시스템이란?
		- 데이터베이스에 데이터를 저장하고, 저장된 데이터를 관리하여 조직에 필요한 정보를 생성해주는 시스템.
		  * 데이터베이스 vs 데이터베이스 관리 시스템 vs 데이터베이스 시스템
		    1. 데이터베이스 : 데이터를 저장해두는 곳(=집합)
		    2. 데이터베이스 관리 시스템 : 데이터베이스에 저장된 데이터가 일관되고 무결한 상태로 유지되도록 관리하는 역할을 하는 것 
		    3. 데이터베이스 시스템 : 데이터베이스와 데이터베이스 관리 시스템을 이용해 조직에게 필요한 정보를 제공해주는 전체 시스템 
		  
---
- 데이터베이스의 구조

	1. 스키마
		- 데이터베이스에 저장되는 데이터 구조와 제약조건의 정의
		  * 인스턴스(=instance) : 스키마에 따라 데이터베이스에 직접 저장된 값
		    - 스키마는 한 번 저장되면 잘 바뀌지 않지만 **인스턴스는 계속 변하는 특성을 가짐**
		 
	2. 3단계 데이터베이스 구조: 내부 -> 외부 단계로 갈수록 추상화 레벨이 높아진다. 
		- 외부단계 
		  * 개별 사용자 관점
		  * 집주인 관점 : 우리 집만 알면 돼.
		  * 외부 스키마(=서브 스키마) : 외부 단계에서 사용자에게 필요한 데이터베이스를 정의한 것으로 **사용자마다 다르다**
		- 개념단계
		  * 조직 전체의 관점
		  * 관리인 관점 : 아파트 전체를 알아야 하지만 아파트의 구조까지 알 필요가 없음.
		  * 개념 스키마 : 모든 사용자에게 필요한 데이터를 통합하여 전체 데이터베이스의 논리적 구조를 정의한 것으로 **하나다**
		- 내부단계
		  * 물리적인 저장 장치의 관점 
		  * 건설 업체 관점 : 아파트의 뼈대와 같은 가장 많고 전체적인 정보를 알아야 함.
		  * 내부 스키마 : 데이터 저장하는 레코드의 구조, 레코들르 구성하는 필드의 크기, 인덱스를 이용한 레코드의 접근 경로 등을 정의한 것으로 **하나다*

  하나의 데이터베이스에는 세 가지 유형의 스키마가 존재하지만, 각각의 스키마는 관점이 다를 뿐 같은 데이터베이스를 일컫는다. 
  
  따라서 스키마는 유기적인 대응 관계가 존재하고 스키마 사이의 대응 관계를 **사상 or 매핑**이라고 한다.
  
  매핑을 통해 ***데이터의 독립성***을 이륙할 수 있다.
  
   3. 데이터 독립성
     - 논리적 데이터 독립성 : 개념 스키마가 변경돼도 외부 스키마는 영향을 받지 않는다.
     - 물리적 데이터 독립성 : 내부 스키마가 변경돼도 개념 스키마는 영향을 받지 않는다. (=저장 인터페이스)

  4. 데이터 사전(=시스템 카탈로그, 메타 데이터)
     - 매핑 정보도 따로 저장될 필요가 있기에 데이터에 관한 정보를 저장하는 곳을 일컫는다.
     - 스키마, 사상 정보, 다양한 제약조건 등
---

- 데이터베이스 사용자 : 데이터베이스를 이용하기 위해 접근하는 모든 사람

- 목적에 따라
	1. 데이터베이스 관리자
		- 데이터베이스 시스템을 운영 및 관리
		- 사용 < 구축, 관리
      * 데이터베이스 구성 요소 선정
      * 데이터베이스 스키마 정의
      * 물리적 저장 구조와 접근 방법 결정
      * 무결성 유지를 위한 제약 조건 정의
      * 보안 및 접근 권한 정책 결정
      * 백업 및 회복 기법 정의
      * 시스템 데이터베이스 관리
      * 시스템 성능 감시 및 성능 분석
      * 데이터베이스 재구성
  2. 최종 사용자(=일반 사용자)
    - 데이터를 조작하기 위해 접근하는 사람들
    - 전문 지식이 없어도 된다.
    - 응용 프로그램을 통해 데이터베이스를 사용한다. (메뉴나 GUI)
  4. 응용 프로그래머
    - 프로그래밍 언어로 데이터 조작어를 삽입하는 사용자.
		
---
- 데이터 언어

    1. 데이터 정의어(DDL)
      - 새로운 데이터베이스를 구축하기 위해 스키마를 정의하거나 기존의 스키마의 정의를 삭제 또는 수정하기 위해 사용하는 데이터 언어
      - 데이터 사전에 반영된다.
		2. 데이터 조작어(DML)
		  - 사용자가 데이터의 삽입 * 삭제 * 수정 * 검색 등의 처리를 데이터베이스 관리 시스템에 요구하기 위해 사용하는 데이터 언어
		  - 사용자가 실제 데이터 값을 활용하기 위해 사용하는 것이다. 
		    * 절차적 데이터 조작어 : 사용자가 어떤 데이터, 어떻게 처리해야하는 지 설명한다. 
		    * 비절차적 데이터 조작어(=선언적 언어) : 사용자가 어떤 데이터가 필요한지만 설명하고 어떻게 처리해야하는 지는 데이터베이스 관리 시스템에 맡긴다.
		3. 데이터 제어어(DCL)
		  - 데이터베이스에 저장된 데이터를 여러 사용자가 무결성과 일관성을 유지하며 문제없이 공유할 수 있도록, 내부적으로 필요한 규칙이나 기법을 정의하는 데 사용하는 데이터 언어
		  - 무결성, 보안, 회복 ,동시성을 보장하게 하기 위해서

    
---
- 데이터베이스 관리 시스템의 구성 : 사용자와 데이터베이스 사이에 위치한다. 
  1. 질의 처리기
    - 사용자의 데이터 처리 요구를 해석하여 처리하는 역할
    - 구성요소 : DDL 컴파일러, DML 프리 컴파일러, DML 컴파일러, 런타임 데이터베이스 처리기, 트랜잭션 관리자
  2. 저장 데이터 관리자
    - 디스크에 저장된 데이터베이스와 데이터 사전을 관리하고 접근하는 역할
    - *운영체제*의 도움을 받는다. 
---


[참조] 데이터베이스개론 (저자: 김연희)
