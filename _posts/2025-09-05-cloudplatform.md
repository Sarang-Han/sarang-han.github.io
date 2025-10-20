---
title: "2강 Cloud Platform, AWS Intro"
description: 25-2 Cloud Computing - 클라우드 플랫폼과 AWS 소개
date: 2025-09-05
categories: [Cloud Computing]
tags: [Cloud]
image: /assets/img/posts/lec3.png
---

## **목차**

1. [Cloud Platforms의 정의](/posts/cloudplatform/#cloud-platforms의-정의)
2. [Tree Common Types](/posts/cloudplatform/#three-common-types)
3. [Cloud Deployment Models](/posts/cloudplatform/#cloud-deployment-models)
4. [Amazon Web Service Intro](/posts/cloudplatform/#amazon-web-service-intro)


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


---


## **Cloud Deployment Models**

> **Who can become a customer of the cloud?**
> 클라우드의 고객이 될 수 있는 주체는 누구일까?


| 구분 | 설명 | 대표 사용 주체 | 장점 | 단점 | 예시 |
|------|------|----------------|------|------|------|
| **Public Cloud** | 누구나 접근 가능한 상업용 클라우드 | 개인, 스타트업, 기업 | 저비용, 확장성, 접근성 | 보안/통제 한계 | AWS, Azure, GCP |
| **Community Cloud** | 여러 조직 공동 사용 클라우드 | 정부, 연구기관, 대학 | 공동 관리, 보안 강화 | 유연성 제한 | Google Gov Cloud |
| **Private Cloud** | 단일 조직 내 전용 클라우드 | 대기업, 금융기관 | 높은 보안, 완전한 통제 | 비용↑, 확장성↓ | 내부 데이터센터 |


---


## **Amazon Web Service Intro**

### **What is AWS?**

> **AWS (Amazon Web Services)**는 아마존이 제공하는 **클라우드 서비스 플랫폼**으로, 사용자는 자신의 비즈니스나 조직의 요구에 맞게 다양한 서비스를 조합하여 사용할 수 있음


### **Major AWS Services**
> AWS는 IaaS부터 PaaS, 그리고 Serverless까지 폭넓은 서비스를 지원함

| 서비스 | 이름(풀네임) | 주요 기능 |
|--------|---------------|------------|
| **EC2** | Elastic Compute Cloud | 가상 서버(VM) 제공, CPU/메모리/GPU 구성 가능 |
| **Lambda** | AWS Lambda | 서버리스(Serverless) 컴퓨팅 – 서버 관리 없이 코드 실행 |
| **S3** | Simple Storage Service | 객체(Object) 기반 스토리지, 높은 내구성 |
| **EBS** | Elastic Block Store | EC2 인스턴스를 위한 블록 스토리지 |
| **RDS** | Relational Database Service | 관리형 관계형 DB (MySQL, PostgreSQL 등) |
| **DynamoDB** | Dynamo Database | 완전 관리형 NoSQL DB |
| **VPC** | Virtual Private Cloud | 격리된 가상 네트워크 환경 제공 |
| **IAM** | Identity and Access Management | 세밀한 접근 권한 제어 및 사용자 관리 |


### **Some History of AWS**

| 연도 | 사건 | 설명 |
|------|------|------|
| **2002.07** | Amazon Web Services 최초 공개 | 외부 사이트가 Amazon 상품을 검색/표시할 수 있는 API 제공 (XML, SOAP 기반) |
| **2006.03** | **Amazon S3 출시** | ‘Pay-per-use’ 요금제 도입 → 클라우드 업계의 기본 모델이 됨 <br> $0.15/GB 저장, $0.20/GB 전송 |
| **2006.08** | **EC2 출시** | 핵심 컴퓨팅 인프라(가상 서버) 공개 |
| **2008–2013** | Google App Engine, Azure, Google Compute Engine 등장 | 클라우드 경쟁 본격화 |


### **Why AWS?**

- **여러 클라우드 제공자 중 하나지만, 시장 점유율 약 33%**
  - 주요 경쟁자: Microsoft Azure, Google Cloud
- **표준화된 클라우드 규격은 존재하지 않음**
  - 초기엔 MS와 Google이 PaaS 중심 → 점차 IaaS까지 확대
  - AWS는 IaaS + PaaS를 모두 지원하며, 가장 다양한 선택지를 제공


### **AWS Global Infrastructure**

AWS는 전 세계를 **Region(지역)** 단위로 나누어 자원을 제공한다.

#### **Region (리전)**
- 각 리전은 서로 다른 지역(예: 서울, 도쿄, 오하이오 등)에 위치
- 데이터 주권(Data sovereignty) 문제 해결에 유리
- 리전별로 요금이 다름
- High Availability, (Fault Tolerance, Low Latency 보장

#### **Availability Zone (AZ)**
- 하나의 리전은 **여러 개의 AZ**로 구성 (보통 2~4개)
- 각 AZ는 독립된 전력, 네트워크, 냉각 시스템을 가진 데이터센터
- 장애가 한 AZ에 발생해도, 다른 AZ가 자동으로 대체
- 예시: `ap-southeast-2a`, `ap-southeast-2b`


### **Interacting with AWS**

AWS를 사용하는 방법 세 가지:

| 도구 | 설명 | 특징 |
|------|------|------|
| **AWS Management Console** | 웹 기반 GUI (브라우저 접속형) | 설치 불필요, 가장 빠르게 시작 가능 |
| **AWS CLI (Command Line Interface)** | 명령줄 기반 도구 | 터미널에서 여러 서비스 일괄 관리 가능 |
| **AWS SDKs (Software Development Kits)** | 프로그래밍 언어용 라이브러리 | 애플리케이션 코드에서 직접 AWS 리소스 제어 가능 |
