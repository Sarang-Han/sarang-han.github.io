---
title: "1강 Cloud Infrastructure"
description: 25-2 클라우드 컴퓨팅 내용 정리
date: 2025-09-02
categories: [Cloud Computing]
tags: [Cloud]
---


## **목차**

1. [Cloud Computing의 정의](/posts/cloudinfra/#cloud-computing의-정의)
2. [On-Premise의 문제점](/posts/cloudinfra/#on-premise의-문제점)
3. [Cloud의 장점](/posts/cloudinfra/#cloud의-장점)
4. [Cloud의 단점](/posts/cloudinfra/#cloud의-단점)
5. [Cloud Infrastructure](/posts/cloudinfra/#cloud-infrastructure)

## **Cloud Computing의 정의**

> **Cloud computing** is a model for enabling ubiquitous, convenient, on-demand **network access to** a shared pool of configurable **computing resources** (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction
> 

⇒ Computing을 **하나의 자원**(as a utility)로 보는 관점

- 클라우드 컴퓨팅은 언제 어디서나 편리하게 필요할 때 즉시 **네트워크를 통해** 접속할 수 있는 컴퓨팅 모델
- 네트워크, 서버, 저장소, 애플리케이션, 서비스 등과 같은 구성 가능한 컴퓨팅 자원들을 공유 pool 형태로 제공하며, 이 자원들을 빠르게 **할당(Provisioning)** 하고 **해제(Release)** 할 수 있음
- 또한 이를 사용하는 과정에서 복잡한 관리 노력이나 서비스 제공자와의 직접적인 상호작용이 거의 필요 없음

### 5가지 핵심 속성

- **On-demand self-service** : 사용자가 필요할 때 원하는 만큼의 컴퓨팅 자원을 직접 요청하고 즉시 이용할 수 있음
- **Broad network access** : 인터넷을 통해 다양한 기기(노트북, 스마트폰, 태블릿 등)에서 언제 어디서나 접근할 수 있음
- **Resource pooling** : 서비스 제공자가 여러 사용자를 위해 하나의 큰 자원 풀을 운영하고, 필요에 따라 동적으로 자원을 배분함
- **Rapid elasticity** : 사용자의 수요 변화에 맞춰 자원을 신속하게 확장하거나 축소할 수 있음
- **Measured service** : 클라우드 시스템이 자원 사용량을 자동으로 모니터링하고 정확히 측정함



## **On-Premise의 문제점**

1. **부하(Load)가 시간대나 상황에 따라 크게 달라지기 때문에 적절한 서버 용량을 미리 정하기가 어렵다**
    <img src="/assets/img/posts/scale.png" alt="provisioning" width="600">
    - 예를 들어, 낮 시간대에는 더 많은 사용자가 서비스를 이용할 수 있음
    - 이 문제를 해결하는 두가지 방법:
        - 최대 부하(피크 타임)에 맞춰 자원을 미리 준비하기 → 항상 자원이 충분하지만, 한가한 시간대에는 낭비가 발생함
        - 최대 부하보다 낮게 자원을 준비하기 → 비용은 절약되지만, 사용자가 몰릴 때는 서비스가 느려지거나 멈출 수 있음

2. **온프레미스를 구축하고 운영하는 것은 매우 비싸다**
    - 많은 **하드웨어 비용**이 필요
    - **전문적인 기술**이 필요
    - 지속적인 **유지보수**가 필요


## **Cloud의 장점**

## **Cloud의 단점**

## **Cloud Infrastructure**