# TextMining Term Project

본 프로젝트는 홍익대학교 산업데이터공학과 **텍스트마이닝 수업의 Term Project**로 진행되었습니다.

FOMC 텍스트와 미국 국채 금리 데이터를 활용해 금리시장 반응을 분석하고,
시장 국면에 따른 금융 포트폴리오 배분 전략을 제안하는 텍스트마이닝 프로젝트입니다.

본 프로젝트는 FOME Statement 및 Minutes의 문장 및 단어 패턴을 분석하고,
미국 국채 금리커브 변화와 연결하여 정책 커뮤니케이션이 시장에 미치는 영향을 정량적으로 해석하는 것을 목표로 합니다.

---

## Project Overview

- FOMC Statement / Minutes 텍스트 데이터 수집 및 전처리
- 미국 국채 만기별 금리 데이터를 활용한 금리커브 구성
- PCA 기반 금리커브 요인 분해 및 정책 서프라이즈 라벨링
- TF-IDF, LDA, BERT, FinBERT 기반 텍스트 모델링
- FOMC 텍스트 기반 시장 레짐 분석
- 분석 결과를 바탕으로 금융 포트폴리오 배분 전략을 제안하는 FedWatch AI 대시보드 구현

---

## Tech Stack

- Python
- Scikit-learn
- BERT, FinBERT, TF-IDF, LDA, PCA, K-means, GMM
- PyTorch
- Hugging Face Transformers
- Next.js
- React

---


## File Description

> 전체 프로젝트 결과는 **[TDM_Final_Presentation.pdf](./TDM_Final_Presentation.pdf)** 에서 확인할 수 있습니다. 

| File | Description |
| --- | --- |
| `01_tone_index_dictionary.ipynb` | Hawkish / Dovish 키워드 사전 구축 및 Tone Index 계산 |
| `02_policy_surprise_modeling.ipynb` | 금리커브 PCA, 정책 서프라이즈 라벨링, 텍스트 기반 분류 모델링 |
| `03_xai_analysis.ipynb` | 모델 해석 및 주요 Hawkish / Dovish 키워드 분석 |
| `04_visualization.ipynb` | 분석 결과 시각화 및 발표자료용 그래프 생성 |
| **[`TDM_Final_Presentation.pdf`](./TDM_Final_Presentation.pdf)** | **최종 발표자료(프로젝트의 전체 분석 과정, 주요 결과, 대시보드 포함)** |
| `TDM_Proposal_Presentation.pdf` | 프로젝트 주제 제안 발표자료 |
---

## Analysis Pipeline

### 1. Tone Index Dictionary

FOMC 텍스트에서 통화정책 방향성을 나타낼 수 있는 Hawkish / Dovish 키워드를 정의하고,  
긍정·부정 수식어와 함께 문장 단위 Tone Index를 계산했습니다.

### 2. Policy Surprise Labeling

미국 국채 만기별 금리 데이터를 활용해 날짜별 금리커브를 구성했습니다.  
이후 PCA를 통해 금리커브 변화를 Level, Slope, Curvature 요인으로 분해하고,  
FOMC 전후 변화량을 기준으로 Hawkish / Dovish / Neutral 라벨을 생성했습니다.

### 3. Text Modeling

FOMC Statement와 Minutes를 다양한 방식으로 벡터화하고,  
텍스트 정보가 금리시장 반응을 어느 정도 설명하는지 비교했습니다.

사용한 주요 텍스트 표현 방식은 다음과 같습니다.

- Tone Index
- TF-IDF
- LDA Topic Vector
- BERT
- FinBERT

### 4. XAI Analysis

분류 모델이 Hawkish / Dovish 판단에 활용한 주요 단어를 분석했습니다.  
이를 통해 어떤 표현이 금리시장 반응과 연결되는지 해석 가능한 형태로 정리했습니다.

### 5. Dashboard Prototype

분석 결과를 바탕으로 FOMC 텍스트를 입력하면  
시장 국면을 분류하고 금융 포트폴리오 배분 전략을 제안하는 대시보드를 구현했습니다.

---

## Results

- FOMC 텍스트와 금리시장 반응 간의 관계를 정량적으로 분석
- PCA 기반 금리커브 요인 분해를 통해 정책 서프라이즈 라벨 생성
- 전통 텍스트 피처 기반 모델에서 Beta 기준 약 0.72 수준의 성능 확인
- Statement와 Minutes를 함께 사용할 때 단독 문서 대비 성능 개선
- FinBERT 임베딩 기반 시장 레짐 분석을 통해 주요 경제 국면과의 정합성 확인
- 분석 결과를 FedWatch AI 대시보드 형태로 확장

---

## How to Run

Jupyter Notebook 환경에서 각 노트북을 실행할 수 있습니다.

```bash
pip install pandas numpy scikit-learn matplotlib seaborn torch transformers
```

권장 실행 순서는 다음과 같습니다.

```text
1. 01_tone_index_dictionary.ipynb
2. 02_policy_surprise_modeling.ipynb
3. 03_xai_analysis.ipynb
4. 04_visualization.ipynb
```

---

## Presentation

- [Final Presentation](./TDM_Final_Presentation.pdf)
- [Proposal Presentation](./TDM_Proposal_Presentation.pdf)

---

## Note

This project was conducted for academic purposes.  
The portfolio allocation strategy suggested in this project is not financial advice.
