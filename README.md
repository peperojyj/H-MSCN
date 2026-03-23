# MSCN 구현 및 Attention 기반 개선 시도

## Overview

MSCN(Multi-Set Convolutional Network)을 기반으로
SQL query의 cardinality estimation 모델을 구현하고,
predicate와 join 간 상호작용을 더 잘 반영하기 위해 attention mechanism을 추가한 프로젝트입니다.

본 프로젝트는 **논문 구현(reproduction) → 구조 이해 → 개선 시도**를 목표로 진행되었습니다.

---

## What I Did

* MSCN 구조 재현 (set-based encoding + MLP aggregation)
* query를 **samples / predicates / joins**로 분리하여 처리
* bitmap 기반 feature encoding 및 normalization 구현
* PyTorch 기반 모델 및 학습 파이프라인 구축

---

## Extension (Attention)

기존 MSCN은 평균 기반 aggregation을 사용하기 때문에
predicate와 join 간 관계를 충분히 반영하기 어렵다고 판단했습니다.

이를 개선하기 위해:

* predicate / join 각각에 **self-attention** 적용
* predicate–join 간 **cross-attention** 추가
* attention을 통해 중요한 요소에 더 높은 weight를 부여하도록 설계

---

## Tech Stack

* Python
* PyTorch
* NumPy

---

## Status

* MSCN baseline 재현 완료
* Attention 기반 확장 구현 (진행형 실험 단계)
