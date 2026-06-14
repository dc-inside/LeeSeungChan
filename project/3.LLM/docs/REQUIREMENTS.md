# 📝 요구사항 분석서 (Requirements Analysis Document)

## 📌 1. 프로젝트 개요
* [cite_start]**목적:** 일반인이 이해하기 어려운 법률 용어, 판결문, 계약서 조항 등을 LLaMa 3.2 3B 모델을 활용하여 일상적인 언어로 쉽게 풀이하고 요약하는 AI 챗봇 서비스 구축을 목적으로 합니다[cite: 5, 13, 53].
* [cite_start]**시스템 아키텍처:** 1차 프로젝트(Navi Bar)와 연동하여, REST API 기반으로 클라우드 Ubuntu의 Flask 서버에서 LLM 추론 결과를 반환하는 구조입니다[cite: 36, 54].

---

## 👥 2. 사용자 유형
* [cite_start]**일반 사용자:** 법률 지식이 부족하여 계약서나 판례 해석에 어려움을 겪는 개인입니다[cite: 37, 55].
* [cite_start]**시스템 관리자:** LLM 모델의 성능을 모니터링하고 파인튜닝 데이터를 업데이트하는 역할을 수행합니다[cite: 38, 56].

---

## ⚙️ 3. 기능 요구사항 (Functional Requirements)
> [cite_start]**Note:** 본 항목은 시스템이 실행해야 하는 핵심 기능을 선언하는 단계입니다[cite: 75, 76]. [cite_start]세부적인 UI 동작 및 예외 처리는 추후 '기능명세서'에서 상세히 다룹니다[cite: 77, 78, 85].

| ID | 요구사항 명 | 세부 설명 |
| :--- | :--- | :--- |
| **FR-01** | 텍스트 입력 | [cite_start]사용자는 1차 프로젝트 UI를 통해 최대 정해진 글자 수(OOO자) 이내의 법률 원문(판례, 조항 등)을 입력할 수 있어야 합니다[cite: 58]. |
| **FR-02** | 데이터 전송 | [cite_start]입력된 데이터는 REST API를 통해 JSON 형태로 Flask 백엔드 서버로 POST 전송되어야 합니다[cite: 59]. |
| **FR-03** | AI 요약 및 풀이 | [cite_start]전송된 텍스트는 로드된 파인튜닝 LLaMa 3.2 3B 모델의 추론(Inference)을 거쳐 일상어로 요약된 결과물로 반환되어야 합니다[cite: 60]. |
| **FR-04** | 자동 면책 조항 삽입 | [cite_start]챗봇의 응답 결과 하단에는 면책 조항(Disclaimer) 문구가 하드코딩되어 강제 출력되어야 합니다[cite: 21, 61]. |

---

## ⚠️ 4. 비기능 요구사항 (Non-Functional Requirements)

| ID | 요구사항 명 | 세부 설명 |
| :--- | :--- | :--- |
| **NFR-01** | 신뢰성(Reliability) 확보 | [cite_start]법률적 사실과 다른 내용을 지어내는 환각(Hallucination) 현상을 최소화해야 합니다[cite: 64]. |
| **NFR-02** | 응답 속도 | [cite_start]사용자가 텍스트를 입력한 후, 모델 추론을 거쳐 결과를 화면에 띄우기까지 목표 시간(O초) 이내에 완료되어야 합니다[cite: 65]. |
| **NFR-03** | 위험 관리(Risk Management) | [cite_start]AI의 답변이 실제 법적 조언으로 오인되는 것을 막기 위한 안전장치(Compliance)를 마련해야 합니다[cite: 66]. |

---

## 📊 5. 데이터 요구사항 (Data Requirements)
* [cite_start]**포맷:** 학습 데이터는 Alpaca 데이터셋 구조(`Instruction`, `Input`, `Output`)를 준수해야 합니다[cite: 67].
* [cite_start]**내용 구성:** `Input` 영역에는 실제 법률 조항이나 판례 원문을 배치하고, `Output` 영역에는 이를 쉽게 풀어쓴 요약본을 넣어 파인튜닝을 진행합니다[cite: 68].

---

## 🚫 6. 제약사항 (Constraints)
* [cite_start]**리소스 한계:** 클라우드 Ubuntu 환경의 VRAM 제약을 고려하여, 4-bit 또는 8-bit 양자화(Quantization)를 적용하고 LoRA 기법을 통한 부분 가중치 학습만을 수행합니다[cite: 8, 69].
* [cite_start]**법적 한계:** AI의 답변은 특정 개인의 상황에 대한 맞춤형 법률 상담(Legal Advice)을 제공해서는 안 되며, 변호사법 위반을 방지하기 위해 일반적인 '문서 해석 및 요약'에만 국한해야 합니다[cite: 70].

---

## 🎯 7. AI 모델 평가 기준 (Evaluation Metrics)
* [cite_start]**정량적 평가:** 훈련 과정에서 텐서보드(Tensor Board)를 활용하여 훈련 손실(Training Loss)과 검증 손실(Validation Loss)이 안정적으로 하락하는지 모니터링합니다[cite: 71].
* [cite_start]**정성적 평가:** 샘플 법률 문서를 50개 선정하여 테스트를 진행하며, 생성된 요약본에 논리적 오류가 있거나 사용자에게 치명적인 독소조항을 누락하지 않았는지 사람이 직접 교차 검증합니다[cite: 72].

---
### 💡 챗봇 응답 강제 출력 문구 (FR-04 반영)
> [cite_start]"본 답변은 AI가 작성한 참고용이며, 실제 법적 효력을 갖지 않습니다. 정확한 판단은 법률 전문가와 상담하십시오." [cite: 20, 61]