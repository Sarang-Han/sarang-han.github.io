---
title: "3강 Virtualization"
description: 25-2 Cloud Computing - 가상화
date: 2025-10-20
categories: [Cloud Computing]
tags: [Cloud]
image: /assets/img/posts/lec4.png
---

## **목차**

1. [What is OS?](/posts/virtualization/#what-is-os)
2. [What is Virtualization?](/posts/virtualization/#what-is-virtualization)
3. [How Virtualization Works?](/posts/virtualization/#how-virtualization-works)


## **What is OS?**

OS는 하드웨어를 관리하고, 응용 프로그램이 이를 효율적으로 사용할 수 있도록 하는 소프트웨어임.
즉, 하드웨어와 애플리케이션 사이의 중간 계층(Indirection Layer) 역할을 함.

### **Regluar Machine Stack**

현대의 컴퓨터 시스템은 아래와 같은 계층적 구조(stack)로 구성되어 있음.

<img src="/assets/img/posts/machine.png" alt="Regluar Machine Stack" width="500">

### **Privilege Level**

| 구분 | 실행 주체 | 설명 |
|------|------------|------|
| **Privileged Instructions** | 운영체제 | 하드웨어 직접 제어 가능 |
| **Unprivileged Instructions** | 애플리케이션 | 제한된 연산만 수행 가능, 하드웨어 접근 시 **시스템 호출(System Call)** 필요 |

### **Typical OS Structure**

운영체제는 **응용 계층 → 라이브러리 → 커널 계층**의 구조로 이루어짐.
각 계층은 서로 다른 역할을 맡으며, 아래로 갈수록 하드웨어와 더 가까워짐.

<img src="/assets/img/posts/typical.png" alt="Typical OS" width="500">

| 계층 | 작성 주체 | 역할 / 내용 |
|------|------------|-------------|
| **Application** | 프로그래머가 작성 | 사용자와 직접 상호작용. 운영체제 기능을 시스템 호출(System Call)이나 라이브러리를 통해 사용 |
| **Libraries** | 전문가(gurus)가 제작 후 제공 | OS 기능을 손쉽게 사용할 수 있도록 도와주는 API 모음. 컴파일 시 링크(link)되어 실행 파일에 포함됨 |
| **Portable OS Layer** | 운영체제의 상위 부분 | 시스템 호출의 내부 로직, 고수준 코드 포함. 하드웨어에 의존하지 않으며 여러 기기에서 재사용 가능 |
| **Machine-dependent Layer** | 운영체제의 하위 부분 | 실제 하드웨어와 직접 상호작용 (드라이버, 인터럽트, 프로세서 제어 등) |

### **Dual-Mode Operation**

운영체제는 시스템 자원을 보호하기 위해 두 가지 실행 모드를 사용함.
OS는 공유 자원(Shared Resources)을 여러 프로그램이 동시에 사용하도록 관리해야 함. 이때 프로그램들이 서로 침범하지 않도록 보호가 필요함.
따라서 권한 수준(Privilege Level)을 구분해, 일반 프로그램은 제한된 명령만 실행하게 함.

<div style="display: flex; align-item: center;">
<img src="/assets/img/posts/dualmode.png" alt="dual mode" width="350">
<img src="/assets/img/posts/transition.png" alt="transition" width="500">
</div>

| 구분 | 설명 |
|------|------|
| **User Mode (사용자 모드)** | 애플리케이션이 동작하는 영역. 하드웨어에 직접 접근 불가. 오직 “비특권 명령(non-privileged instructions)”만 실행 가능. |
| **Kernel Mode (커널 모드)** | 운영체제가 동작하는 영역. 모든 자원과 명령어에 접근 가능. “특권 명령(privileged instructions)”을 실행함. |

### **Interrupt**

인터럽트는 CPU가 즉시 반응해야 하는 이벤트를 처리하기 위한 핵심 메커니즘을 의미함.
OS는 이를 통해 동시성(Concurrency)과 반응성(Responsiveness)을 보장함.


| 구분 | 발생 원인 | 예시 |
|------|------------|------|
| **Hardware Interrupt** | 외부 장치의 신호에 의해 발생 | 키보드 입력, 마우스 클릭, 네트워크 패킷 수신, 타이머 신호 등 |
| **Software Interrupt** | 프로그램 내부에서 발생 | **Exception**: 0으로 나누기 오류 등, **System Call**: OS 기능 요청 (파일 입출력 등) |

운영체제는 인터럽트가 발생했을 때 다음 순서로 처리함:

1. 새로운 인터럽트 잠시 비활성화 (Disable interrupts)
2. 현재 명령어의 주소 저장 (Save PC)
3. 인터럽트 서비스 루틴(Interrupt Service Routine) 실행 (Transfer control)
4. CPU 상태 저장 및 복원 (Save/Restore CPU State)
5. 인터럽트 재활성화 (Re-enable interrupts)
6. 중단된 명령 재개 (Resume execution)

### **왜 컴퓨터 구조, 운영체제, 인터럽트를 먼저 배우는가?**

Virtualization는 운영체제가 하던 ‘자원 가상화’와 ‘제어권 관리’를 한 단계 확장하여, 하나의 하드웨어 위에서 여러 운영체제가 동시에 동작하도록 만드는 기술이기 때문임.


#### 컴퓨터 구조
- CPU, 메모리, 디스크 등 물리적 자원 구조 이해가 필수.
- 가상화는 결국 이 하드웨어 자원을 흉내 내는 기술이기 때문.

#### 운영체제
- 이미 OS 자체가 하드웨어의 가상화를 수행하고 있음.
  - CPU 스케줄링 → 여러 프로그램이 동시에 실행되는 것처럼
  - 메모리 관리 → 각 프로그램이 독립된 메모리를 가진 것처럼
- 즉, 가상화의 1세대 모델이 바로 OS.

#### 인터럽트
- CPU 제어권을 전환하는 메커니즘.
- OS가 프로그램 ↔ 하드웨어 간 제어를 주고받을 수 있게 해줌.
- 가상화에서는 하이퍼바이저가 이 제어권을 '가로채서' 여러 OS에 분배 함.

---


## **What is Virtualization?**

Virtualization은 **물리적 자원을 논리적으로 분리**하고, 여러 개의 가상 환경을 만들어내는 기술임. 쉽게 말해, **하나의 컴퓨터를 여러 대처럼** 보이게 하는 것이 바로 가상화임.

### **핵심 개념 3가지**

- **Abstraction (추상화)**:
  - 물리적 하드웨어를 운영체제나 애플리케이션으로부터 **분리(Decoupling)** 하는 것
  - 하나의 CPU/메모리를 여러 가상 머신(VM)이 공유하지만, 각 VM은 자신만의 컴퓨터처럼 인식
- **Isolation (격리)**:
  - 각 가상 머신이 서로 **독립적으로 동작**하도록 하는 것
  - 한 VM이 다운되거나 보안 침해를 당해도 다른 VM에는 영향 없음
- **Resource Sharing (자원 공유)**:
  - 여러 가상 머신이 하나의 물리적 하드웨어 자원을 효율적으로 나누어 사용
  - CPU, 메모리, 디스크를 여러 VM이 동시에 활용 → 비용 절감 + 효율 극대화

### **예시**

- 실제 서버 1대 위에서
  - VM1: Ubuntu (웹 서버)
  - VM2: Windows (데이터베이스 서버)
  - VM3: CentOS (개발용 환경)
- 를 동시에 실행할 수 있다.

### **클라우드 컴퓨팅에서의 중요성**

클라우드 컴퓨팅의 핵심 기반 기술은 바로 **가상화(Virtualization)**임.
클라우드 서비스 제공업체는 가상화를 통해 물리적 서버 자원을 효율적으로 활용하고, 고객에게 유연한 컴퓨팅 환경을 제공할 수 있음.
=> 클라우드 컴퓨팅은 가상화를 비즈니스 모델로 구현한 결과물임

| 핵심 요소 | 설명 |
|------------|------|
| **Resource Optimization (자원 최적화)** | 가상화는 여러 가상 머신(VM)이 하나의 물리적 서버 자원을 공유하도록 하여 하드웨어 활용률을 극대화. → 놀고 있는 CPU/메모리를 줄여 효율성을 높임. |
| **Cost Efficiency (비용 효율성)** | 물리적 서버를 여러 대 두는 대신, 한 서버 안에서 여러 환경을 실행할 수 있어 하드웨어 구매 및 유지 비용 절감 가능. |
| **Scalability & Flexibility (확장성과 유연성)** | 필요한 만큼 가상 머신을 즉시 생성하거나 제거할 수 있어, 서비스 수요 변화에 빠르게 대응 가능. → 클라우드의 autoscaling 기능의 기반. |
| **Platform Independence (플랫폼 독립성)** | 한 물리적 서버 위에서 여러 운영체제(OS*를 동시에 실행할 수 있음 → Windows, Linux, macOS 환경을 한 인프라에서 함께 운영 가능. |

### **가상화 계층 구조**

가상화는 실제 하드웨어 위에 가상화 계층(VMM)을 두고, 그 위에서 여러 가상 운영체제(Guest OS)와 애플리케이션이 독립적으로 실행되도록 만든 구조임.

Virtualization Stack = Hardware + VMM(Hypervisor) + Guest OS + Applications

<img src="/assets/img/posts/vmm.png" alt="VMM" width="500">

| 계층 | 설명 |
|------|------|
| **Application** | 각 가상 머신(Guest OS) 위에서 실행되는 프로그램. 일반 OS 환경과 동일하게 동작한다. |
| **Guest OS** | 가상 머신 내부에서 실행되는 운영체제. 예: Windows, Linux 등 → 각 Guest OS는 자신이 물리적 하드웨어 위에서 실행 중이라고 착각함. |
| **VMM (Virtual Machine Monitor)** | 하드웨어와 Guest OS 사이의 가상화 계층. 가상 하드웨어를 생성하고, 각 Guest OS가 독립적으로 동작하도록 리소스 분배 및 격리 수행 |
| **Hardware** | 실제 CPU, 메모리, 디스크, 네트워크 장치 등. MM이 이 자원을 관리하고, 가상 자원으로 변환하여 각 Guest OS에 제공. |

### **가상화의 구성 요소**

#### Hypervisor

#### Virtual Machines & Guest OS

## **How Virtualization Works?**
