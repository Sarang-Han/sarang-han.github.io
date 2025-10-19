---
title: "[번역] How To Become A Mechanistic Interpretability Researcher"
description: Neel Nanda의 LessWrong AI Alignment Forum "How To Become A Mechanistic Interpretability Researcher" 글 번역
date: 2025-10-18
categories: [Mechanistic Interpretability]
tags: [Mechanistic Interpretability, AI, Alignment]
image:
---

- 원문: [How To Become A Mechanistic Interpretability Researcher](https://www.lesswrong.com/posts/jP9KDyMkchuv6tHwm/how-to-become-a-mechanistic-interpretability-researcher)
- 저자: Neel Nanda

*마지막 업데이트 2025년 9월 2일*

## TL;DR (요약)

- 이 글은 Mechanistic interpretability 연구를 하고자 하는 사람들을 위해 제가 추천하는 사고방식과 과정을 다룹니다. 명확한 방향성을 제시하기 위해 의견이 담긴 조언과 구체적인 추천을 제공합니다.
  - Mech interp 연구는 투자 대비 효율이 좋고, 영향력이 크며, 짧은 피드백 루프와 적당한 컴퓨팅 자원만으로도 스스로 배울 수 있는 분야입니다.
  - **최소한의 필수 기본기를 익힌 뒤, 바로 연구를 시작하세요**. Mech interp는 경험적 과학(empirical science)입니다.

- **세가지 단계**:
  - [**기초 익히기**](#기초-익히기) (≤ 1개월): 필수 개념을 배우고, 깊이보다는 폭넓게 접근하세요.
  - [**연구 미니 프로젝트로 학습하기**](#연구-미니-프로젝트로-학습하기): 1~5일짜리 미니 프로젝트를 통해 기본적인 연구 기술을 연습하고, 빠른 피드백 루프 기술에 집중하세요.
  - [**본격 프로젝트로 확장하기**](#본격-프로젝트로-확장하기): 1~2주 단위의 연구 스프린트를 수행하고, 그중 잘된 프로젝트를 계속 이어나가세요. 더 깊은 기술과 훌륭한 연구자의 사고방식을 탐구해보세요.

- **Stage 1: 기초 익히기 (Learning the Ropes)**
  - **깊이보다 폭**: 완벽함이 아니라 좋은 기준(Good baseline)을 확보하는 데 집중하세요.
  - **기본기 배우기**: Transformer를 처음부터 직접 구현해보기, 주요 MI 기법 익히기, 연구 분야의 전체적인 지형 파악하기, 선형대수적 직관 키우기, MI 코드 작성법 익히기 ([ARENA는 훌륭한 학습 도구입니다!](https://arena-chapter1-transformer-interp.streamlit.app/))
  - **직접 손을 움직이기**: 읽기만 하지 마세요. Mech Interp는 본질적으로 경험적 과학입니다.
  - **한 달 후에는 다음 단계로 넘어가기**: ‘이제 다 배웠다’는 느낌을 기대하지 말고, 모든 것을 다 익히려 하지 마세요. 필요할 때 더 배우면 됩니다. 실제로 무언가를 시작하지 않으면 위대한 연구에 도달할 수 없습니다.
  - **LLM을 적극적으로 활용하기**: 완벽하지는 않지만, 지금의 당신보다는 Mech interp를 더 잘 다룹니다. 올바르게 사용한다면 핵심적인 학습 도구가 될 것입니다.

- **연구 과정 살펴보기 (Unpacking the research process)**
  - 많은 기술(skill)들이 있으며, 이를 피드백 루프의 속도에 따라 분류할 수 있습니다.
    - 빠른 기술 (몇 분에서 몇 시간 단위): 실험 작성, 실행, 디버깅과 같은 작업
    - 느린 기술 (수 주 단위): 우선순위를 정하거나, 언제 방향을 전환할지 판단하는 능력
    - 매우 느린 기술 (수개월 단위): 좋은 연구 아이디어를 만들어내는 능력
  - **모든 기술을 한꺼번에 배우려 하지 마세요.** 먼저 빠른/중간 속도의 기술에 집중하고, 점차적으로 확장하세요.
  - 연구의 네 단계:아이디어 발굴 (**Ideation**) -> 탐색 (**Exploration**) -> 이해 (**Understanding**) - 가설을 검증하기 -> 정제 및 서술 (**Distillation**)

- **Stage 2: 미니 프로젝트 (Mini projects)** (각각 1–5일 소요, 총 2–4주 동안 수행)
  - **탐색적 사고방식**: 단위 시간당 정보 획득량을 최대화 하세요. 막혔을 때 어떻게 다시 길을 찾는지 배우는 것이 중요합니다. 구체적인 계획이 없어도 괜찮고, 배우고 있다면 충분합니다.
  - **이해 중심 사고방식**: **모든 연구 결과는 증명되기 전까지는 거짓입니다.** (Every research result is false until proven otherwise) 결과가 더 흥미로울수록, 거짓일 가능성은 더 높습니다. 스스로에게 가장 냉정한 비평가가 되세요.
  - 아이디어 구상(ideation)과 글쓰기(distillation)는 아직 우선순위가 아닙니다. 취향(taste)과 우선순위 결정(prioritization)을 **무언가를 직접 해보면서** 배워보세요.
  - 좋은 연구 아이디어를 얻는 데에는 오랜 시간이 걸리니, **초기 프로젝트를 고를 때는 베끼세요!** 예를 들어, 기존 논문을 확장하거나 재현하는 등 범위가 잘 정의된 프로젝트를 선택하세요.
  - LLM을 적극적으로 활용하세요: 연구 및 코딩 속도를 크게 향상시킬 수 있습니다. (올바르게 사용한다면요!)



이어서 업데이트 예정...
