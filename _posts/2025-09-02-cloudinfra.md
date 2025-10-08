---
title: "1강 Cloud Infrastructure"
description: 25-2 Cloud Computing - 클라우드 컴퓨팅 개념과 인프라 구성요소
date: 2025-09-02
categories: [Cloud Computing]
tags: [Cloud]
image: /assets/img/posts/lec2.png
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

- 클라우드 컴퓨팅은 언제 어디서나 편리하게 **네트워크를 통해** 접속할 수 있는 컴퓨팅 모델
- 네트워크, 서버, 저장소, 애플리케이션, 서비스 등과 같은 구성 가능한 컴퓨팅 자원들을 공유 pool 형태로 제공하며, 이 자원들을 빠르게 **Provisioning** 하고 **Release** 할 수 있음
- 사용하는 과정에서 복잡한 관리 노력이나 서비스 제공자와의 직접적인 상호작용이 거의 필요 없음

### 5가지 핵심 속성

- **On-demand self-service** : 사용자가 필요할 때 원하는 만큼의 컴퓨팅 자원을 직접 요청하고 즉시 이용할 수 있음
- **Broad network access** : 인터넷을 통해 다양한 기기(노트북, 스마트폰, 태블릿 등)에서 언제 어디서나 접근할 수 있음
- **Resource pooling** : 서비스 제공자가 여러 사용자를 위해 하나의 큰 자원 풀을 운영하고, 필요에 따라 동적으로 자원을 배분함
- **Rapid elasticity** : 사용자의 수요 변화에 맞춰 자원을 신속하게 확장하거나 축소할 수 있음
- **Measured service** : 클라우드 시스템이 자원 사용량을 자동으로 모니터링하고 정확히 측정함

---

## **On-Premise의 문제점**

1. **부하(Load)가 시간대나 상황에 따라 크게 달라지기 때문에 적절한 서버 용량을 미리 정하기가 어렵다**
    <img src="/assets/img/posts/scale.png" alt="provisioning" width="600">
    - 예를 들어, 낮 시간대에는 더 많은 사용자가 서비스를 이용할 수 있음
    - 이 문제를 해결하는 두가지 방법:
        - 최대 부하(피크 타임)에 맞춰 자원을 미리 준비하기 → 항상 자원이 충분하지만, 한가한 시간대에는 낭비가 발생함
        - 최대 부하보다 낮게 자원을 준비하기 → 비용은 절약되지만, 사용자가 몰릴 때는 서비스가 느려지거나 멈출 수 있음

2. **온프레미스를 구축하고 운영하는 것은 매우 비싸다**
    - 많은 하드웨어 비용이 필요
    - 전문적인 기술이 필요
    - 지속적인 유지보수가 필요

3. **확장(Scaling up)과 축소(Scaling down)가 어렵다**
    - 확장: 새 서버를 주문하고, 기존 클러스터에 통합하는 과정도 오래 걸림. 시스템을 전면 재설계 해야할 수도 있음
    - 축소: 안쓰이는 하드웨어의 처리가 곤란함. 유휴(idle) 상태일때도 전력을 소비하며 고정 비용이 들어감

---

## **Cloud의 장점**

1. **초기 투자비용 감소**: 서버나 소프트웨어를 직접 구매할 필요가 없으므로
2. **사용한 만큼만 지불** (Pay-as-you-go): 실제 사용량에 따라 과금됨
3. **향상된 확장성**(Scalability): 필요할 때 즉시(on-demand) 자원을 동적으로 할당 가능
4. **규모의 경제** (Economies of Scale): 규모가 커질수록 더 저렴하게 쓸 수 있음
5. **가용성**(availability)과 **신뢰성**(reliability): 오랜 시간 동안, 안정적으로 중단없이 서비스 가능
    - ex: AWS의 경우 SLA(service level agreement)를 통해 각 AWS 리전에서 월 가동률 99.99%로 EC2를 이용할 수 있도록 보장함

### Case Study: Animoto (2008)
<img src="/assets/img/posts/animoto.png" alt="animoto case" width="400">

- Animoto는 사용자가 업로드한 사진과 음악으로 자동으로 영상을 만들어주는 서비스임
- 이 서비스는 Amazon EC2 + S3 + SQS를 기반으로 구축되었음
- 2008년 4월 중순, Facebook 앱 버전을 출시했는데 → 단 3일 만에 75만 명 이상의 사용자가 몰려들었음
- 그 결과, EC2 사용량이 50대 서버에서 3,500대 서버로 70배 확장 (x70 scalability)
- 클라우드의 확장성 덕분에, Animoto는 트래픽 증가에도 불구하고 서비스 중단 없이 안정적으로 대응할 수 있었음

---

## **Cloud의 단점**

1. **보안 취약점 증가**: 데이터가 외부에 저장되기 때문에 해킹 위험이 커질 수 있음
2. **운영 통제권 감소**: 운영 및 관리의 일부 주도권을 서비스 제공자에게 넘겨야함
3. **클라우드 간 이동성 제약**: 다른 클라우드 서비스로 옮길 때 호환성 문제나 마이그레이션 비용 발생
4. **다지역 규제 및 법적 문제**: 데이터가 여러 나라에 저장되므로 규제 대응이 복잡해질 수 있음

---

## **Cloud Infrastructure**

### **개요**
- 클라우드의 주요 물리적 구성 요소는 **Server**, **Networking Equipment**, **Storage**
- 인프라는 이런 구성 요소들이 한데 모여있는 **Datacenter** 형태로 구축됨


### **Server**
- 클라이언트(사용자나 다른 시스템)에 서비스를 제공하는 컴퓨터
- 고신뢰성(reliability)과 요청 처리 능력을 위해 설계됨
    - ex: 다중 코어(Multi-core) CPU를 가진 1~2 소켓 서버, 안정성을 위한 ECC 메모리 사용 등
- 최근 변화: AI와 고성능 연산 수요로 인해 GPU, FPGA, AI 전용 accelerator 등이 서버에 탑재되고 있음


### **Blade Server**
- 대규모 환경에서는 공간 절약을 위해 Blade 구조를 사용함
- 좁은 공간에 컴퓨팅 파워를 효율적으로 집약하기 위한 구조임
- 블레이드 서버의 주요 장점:
    - 공간 절약 (Floor space)
    - 관리 용이성 (Manageability)
    - 확장성 (Scalability)
    - 전력 및 냉각 효율 (Power & Cooling)


### **Racks**
<img src="/assets/img/posts/unit.png" alt="provisioning" width="150">

- 블레이드 서버는 랙(rack)이라는 금속 프레임에 장착됨
- 서버는 모듈형(modular)으로 설계되어 랙 단위(“U” 단위)에 맞게 끼워 넣을 수 있음
- 하나의 랙에는 최대 42개의 1U(=1 rack unit) 서버를 장착할 수 있음


### **Heterogeneous Servers**
- 모든 서버가 동일하지는 않음 (not homogeneous)
- 즉, 서버마다 내부 하드웨어 구성이 다를 수 있으며 각 서버는 주요 애플리케이션 유형(예: 데이터베이스, 웹서버, AI 연산 등)에 맞게 최적화된 구성을 가짐 => CPU 중심형 / GPU 중심형 / 메모리 중심형 서버가 혼합


### **Networking**
- 클라우드 자원은 대부분 인터넷을 통해 사용자에게 전달됨
- 이를 위해 제3의 네트워크 서비스 제공자(통신사, 백본 사업자 등)이 구축/유지하는 대규모 네트워크 인프라가 필요함
- 주요 네트워크 장비 구성:
    - 물리 케이블 (Cables)
    - 스위치 (Switches)
    - 무선 액세스 포인트 (Wireless Access Points)


### **Storage**
- 기본 저장장치:
    - 디스크 트레이(HDD), SSD, NVM 플래시 메모리 등
- 스토리지 어레이 (Storage Array):
    - 여러 개의 저장장치를 하나의 대용량 시스템으로 묶은 장치
    - 페타바이트(Petabytes) 단위의 데이터를 중앙에서 관리할 수 있음
    - 여러 서버가 동시에 접근할 수 있도록 전용 네트워크를 통해 공유(storage network)됨


### **Cluster**
- 여러 개의 랙(rack)이 모여 하나의 클러스터(cluster)를 이룸
- 대규모 병렬 처리나 분산 연산을 위해 서버들을 묶은 단위라고 보면 됨


### **Datacenter**
- 여러 클러스터(서버와 스토리지 팜)이 연결되어 형성된 대규모 컴퓨팅 시설
- 규모 예시:
    - 5만~20만 개의 랙(racks)
    - 각 랙당 약 100개의 CPU 코어(core)
    - 전력 소비량: 10~100 메가와트(MW)
    - 저장 용량: 수 제타바이트(ZB, 10^21바이트)
- 데이터 센터의 내부 요소:
    - 서버 랙 (Racks of servers)
    - 네트워크 스위치 (Network switches)
    - 스토리지 어레이 (Storage arrays)
    - 냉각 설비 (Air conditioning / Cooling)
    - 이중화된 전력 공급 (Redundant power): UPS, Generators, Multiple power feeds
    - 화재 방지 시스템 (Fire protection)
    - 물리적 보안 (Physical security)
    - 모니터링 시스템 (Monitoring systems)
- 데이터 센터의 글로벌 분포:
    - 데이터센터는 전세계적으로 분산되어 위치함
    - 사용자와 물리적 거리 단축 -> latentcy를 줄이기 위함
    - 더 저렴한 전력/토지 자원 확보
    - 지역적 장애에 대비한 안전성 확보(failover protection)
- New Trends:
    - 데이터 센터가 점점 AI Factory로 진화하고 있음 (GPU 도입 확대)
    - 아프리카, 라틴아메리카, 중동, 인도 등으로 확산됨 -> 전력/토지 비용이 낮은 곳에 구축 붐
    - Liquid Cooling 도입 확대, ASICs(특정 목적용 반도체) 채택 등
