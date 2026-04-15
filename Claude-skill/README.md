# 📝 paper-writing-assistant

> A Claude skill that automates the research paper writing workflow — from section drafts to iterative feedback loops.

---

## Overview

**paper-writing-assistant**는 Claude용 스킬로, 연구 논문의 섹션별 드래프트 작성부터 자가 리뷰, 사용자 피드백 반영까지의 반복 루프를 자동화합니다. ML/NLP/AI 및 일반 CS 논문을 지원하며, 아이디어 메모나 실험 결과만 있어도 즉시 시작할 수 있습니다.

```
[입력 수집] → [섹션 드래프트] → [자가 리뷰] → [사용자 피드백] → [재작성] → [반복]
```

---

## Features

### 🗂 섹션별 드래프트 자동 생성
Abstract, Introduction, Related Work, Methodology, Experiments, Conclusion 각 섹션에 대한 구조화된 드래프트를 생성합니다. Venue(ACL, NeurIPS, ICML 등)에 맞는 어조와 분량을 자동으로 적용합니다.

### 🔍 자가 리뷰 (Self-Review)
드래프트 생성 후 6개 기준으로 자동 점검합니다:

| 체크 항목 | 설명 |
|-----------|------|
| 논리 흐름 | 문단 간 연결 자연스러운지 |
| Claim 지지 | 모든 주장에 근거(수식/실험/인용) 있는지 |
| 중복 제거 | 반복되는 문장 있는지 |
| 학술 표현 | 구어체, 모호한 표현 없는지 |
| 일관성 | notation이 전체 섹션에서 통일되는지 |
| Venue fit | 형식/분량 기준 충족하는지 |

### 🔄 피드백 루프
자가 리뷰 후 아래 5가지 액션 중 선택:
- **A)** 제안된 수정사항 자동 반영 → 재드래프트
- **B)** 특정 부분만 지정해서 수정
- **C)** 표현 전면 교체 (aggressive rewrite)
- **D)** 다음 섹션으로 이동
- **E)** 현재 섹션 확정 후 전체 논문 조립

### ⚡ 특수 기능

**Reviewer Simulation**
NeurIPS/ACL/ICML 스타일 가상 리뷰 3개 생성 + 각 weakness에 대한 rebuttal 초안 제공.

**Related Work 자동 구조화**
논문 리스트를 넣으면 주제별 클러스터링 → 차이점 요약 → 단락 변환까지 자동 처리.

**실험 결과 → 텍스트 변환**
표/수치 데이터를 입력하면 결과 해석 문장, ablation study 분석 단락을 자동 생성.

---

## Supported Venues

| Venue | 분량 | 특이사항 |
|-------|------|----------|
| ACL / EMNLP / NAACL | 8 pages | Ethics statement 필수 |
| NeurIPS | 9 pages | Broader Impact section 필수 |
| ICML | 8 pages | 수학적 엄밀함 강조 |
| ICLR | 8 pages | Reproducibility 강조, 코드 공개 권장 |
| CVPR / ICCV / ECCV | 8 pages | Figure 품질, 시각적 결과 중시 |

---

## Installation

`.skill` 파일을 Claude에 업로드하거나, Claude.ai 설정의 Skills 섹션에서 설치합니다.

```
paper-writing-assistant.skill
```

---

## Usage

설치 후 아래와 같은 자연어로 트리거됩니다:

```
"Introduction 드래프트 작성해줘"
"Abstract 써줘, NeurIPS 제출용이야"
"Related Work 정리해줘, 논문 리스트 줄게"
"이 실험 결과 표를 논문 텍스트로 바꿔줘"
"리뷰어 시뮬레이션 해줘"
"현재 섹션 피드백해줘"
```

연구 주제, 실험 메모, 아이디어 노트만 있어도 시작할 수 있습니다.

---

## Output Formats

- **기본**: Markdown (GitHub-flavored)
- **LaTeX**: `\section{}`, `\subsection{}` 구조
- **수식**: 항상 LaTeX 형식 (`$$...$$`)
- **인용**: `[Author et al., YEAR]` 형식 (BibTeX key 요청 시 제공)

---

## File Structure

```
paper-writing-assistant/
├── SKILL.md                        # 메인 워크플로우 정의
└── references/
    ├── section-guides.md           # 섹션별 상세 작성 패턴
    └── venue-styles.md             # Venue별 스타일 가이드
```

---

## License

MIT
