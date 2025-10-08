---
title: "2강 Cloud Platform, AWS Intro"
description: 25-2 Cloud Computing - 클라우드 플랫폼과 AWS 소개
date: 2025-09-05
categories: [Cloud Computing]
tags: [Cloud]
image: /assets/img/posts/lec3.png
---

## **목차**

1. [Cloud Platforms의 정의]()
2. [Tree Common Types]()
3. [Cloud Deployment Models]()
4. [Amazon Web Service Intro]()


## **Cloud Platforms의 정의**
- **Cloud Platform**: 클라우드 서비스를 제공하는 시스템 전체를 의미함
- **“Everything as a Service”**: "모든 것을 서비스 형태로 제공한다"는 철학
- 클라우드 서비스의 구분:
    - 클라우드가 **완성된 애플리케이션 전체**를 제공하는가?
    - 아니면 서버나 스토리지 같은 **IT 자원만 제공**하는가?
    - 자원을 제공한다면, 어떤 종류이며 **얼마나 추상화**되어 있는가?

---

## **Three Common Types**

### **Software as a Service (SaaS)**
<img src="/assets/img/posts/saas.png" alt="SaaS" width="300">

> 클라우드 서비스 제공자(CSP, Cloud Service Provider)가 완성된 애플리케이션 전체를 제공한다

- 사용자는 앱을 자신의 컴퓨터에 설치하거나 실행할 필요가 없음
- 모든 관리는 클라우드 제공자가 담당함


### **Platform as a Service (PaaS)**
<img src="/assets/img/posts/paas.png" alt="PaaS" width="300">

> 클라우드 서비스 제공자가 SaaS를 개발 및 운영할 수 있는 플랫폼 환경을 제공한다

- 사용자는 이 플랫폼 위에서 직접 애플리케이션(SaaS 형태)를 개발할 수 있음
- CSP가 하드웨어, OS, 런타임 환경 등 기반 요소를 모두 관리해줌
- 개발자는 App Engine 등의 API나 프레임워크 규칙에 맞게 앱을 작성해야 함


### **Infrastructure as a Service (IaaS)**
<img src="/assets/img/posts/iaas.png" alt="IaaS" width="300">

> 클라우드 서비스 제공자가 서버와 스토리지 같은 기초 인프라 자원 자체를 대여해준다

- Virtualization을 이용해 한 서버를 여러 사용자가 나누어 쓸 수 있도록 함
- 사용자는 새로운 Virtual Machine을 만들 수 있음
- Virtual Machine에는 표준 OS 환경이 제공되며, 그 위에 원하는 소프트웨어를 자유롭게 설정할 수 있음


### **Others**
- “as a Service”의 개념은 SaaS, PaaS, IaaS뿐 아니라 점점 더 다양하게 확장되고 있음
- 예시:
    - **DaaS** (Desktop as a Service): 클라우드에서 원격 데스크톱 환경을 제공
    - **MLaaS** (Machine Learning as a Service): ML 모델 학습 및 배포 환경을 서비스로 제공
    - **DBaaS** (Database as a Service): 데이터베이스를 직접 설치하지 않고 API로 이용


### **요약**

| 구분 | 제공 수준 | 사용자의 역할 | CSP의 역할 | 대표 예시 |
|-|-|-|-|-|
| **SaaS** | 완성된 애플리케이션 | 사용 | 모든 인프라, 플랫폼, 애플리케이션 관리 | Gmail, Google Docs |
| **PaaS** | 개발 플랫폼 | 앱 개발 | 인프라, OS, 런타임, DB 관리 | Google App Engine, Azure |
| **IaaS** | 가상 서버 및 스토리지 | 시스템 구축, 운영 | 물리적 하드웨어 관리 | AWS EC2 |



## **Cloud Deployment Models**


## **Amazon Web Service Intro**

