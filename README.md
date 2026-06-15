# 생성형 AI 기반 서비스 개발자 양성 

독립적인 프로젝트를 통합 관리하는 모노레포 저장소입니다. 
각 프로젝트는 독자적인 Flask 서버와 환경을 가지고 구동됩니다.

---

## 1. 통합 프로젝트 대시보드

| 프로젝트명 | 폴더 경로 | 주요 핵심 기능 | 개발 상태 | 바로가기 링크 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Project 1: Predict** | `/project1-predict` | 영양소 섭취 기반 고콜레스테롤혈증 위험도 예측 및 자가 진단 서비스 | `완료` | [바로가기](./project1-predict/README.md) |
| **Project 2: Vision** | `/project2-vision` | 이미지 기반 객체 탐지 API | `완료` | [바로가기](./project2-vision/README.md) |
| **Project 3: LLM** | `/project3-LLM` | 법률 AI 챗봇 | `진행중` | [바로가기](./project3-LLM/README.md) |

---

## 2. 전체 디렉토리 구조

```text
/ (Root)
├── README.md                          # 통합 메인 문서
│
├── project1-predict/                  # 1차 예측 프로젝트 폴더
│   ├── app.py
│   ├── requirements.txt
│   ├── docs/
│   │   └── REQUIREMENTS_ANALYSIS.md   # 1차 요구사항 분석서
│   └── ...
│
├── project2-vision/                   # 2차 비전 프로젝트 폴더
│   ├── app.py
│   ├── requirements.txt
│   ├── docs/
│   │   └── REQUIREMENTS_ANALYSIS.md   # 2차 요구사항 분석서
│   └── ...
│
└── project3-vision/                   # 3차 비전 프로젝트 폴더
    ├── app.py
    ├── requirements.txt
    ├── docs/
    │   └── REQUIREMENTS_ANALYSIS.md   # 3차 요구사항 분석서
    └── ...
