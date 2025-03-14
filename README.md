# Personalized_outfit_recommendation_and_generation
Recommendation &amp; Ranking, Node2Vec, Association Rule Mining (Apriori algorithm)

## **📑 Summary**

**"오늘 뭐 입지?"**

온라인 쇼핑 사용자들은 수많은 아이템 중에서 자신에게 어울리는 스타일을 찾는 데 어려움을 겪습니다. 이 고민을 해결하기 위해, **사용자 맞춤형 패션 추천 시스템**을 개발하는 프로젝트를 진행했습니다.

사용자가 클릭한 패션 아이템 데이터를 활용해 **개인화된 코디를 추천**하고, 불완전한 코디에서 **누락된 아이템을 자동으로 완성하는 AI 모델**을 구축했습니다. 특히, **Node2Vec을 활용한 그래프 기반 추천 모델과 Apriori 알고리즘을 적용하여 추천 정확도를 향상**시켰으며, 기존 방식보다 **더 정교한 스타일 추천이 가능하도록 개선**했습니다.

---

## **⭐ Key Task**

### **1️⃣ 패션 코디 추천 (Outfit Recommendation) 모델 개발**

✅ **문제 정의**

- 온라인 쇼핑몰에서는 사용자가 다양한 패션 아이템을 탐색하지만,**자신의 스타일과 맞는 코디를 찾는 것이 어려운 문제**가 존재
- 효과적으로 유사한 사용자 / 유사한 아이템 구별할 수 있는 방법 필요
- 기존 협업 필터링(Collaborative Filtering) 방식을 먼저 시도했으나, 데이터에 **신규 사용자, 신규 아이템 데이터**가 많이 포함되어 **Cold Start 문제**로 인해 적절한 추천이 어려움
- Classification에 사용할 효율적인 Threshold 설정 필요

✅ **해결 방법**

- 두 종류의 노드(사용자, 아이템 세트)를 포함하는 **Bipartite Graph**를 생성
- **유사도 분석을 위해 각 사용자, 아이템 별 임베딩 벡터 필요 → Node2Vec 알고리즘**을 적용하여 각 노드(사용자, 아이템)를 **128차원의 벡터로 변환**
- **Cosine Similarity**를 활용하여 특정 사용자와 가장 유사한 50명의 사용자, 특정 아이템 세트와 가장 유사한 100개의 아이템 세트를 탐색
- **효율적인 Threshold 선정**을 위해 **각 Threshold 별 실험 진행** → 최적의 20%로 설정
    - 사용자 A와 가장 유사한 50명의 사용자 중 20% 이상이 아이템 B를 선택했다면, A도 B를 선택했을 것으로 분류

✅ **성과**

- **Accuracy 0.702** 달성 → 기존 모델 성능(랜덤 0.5, 단순 통계 0.615, 협업 필터링 0.479) 대비 성능 향상

---

### **2️⃣ 불완전한 코디 자동 완성 (Outfit Generation) 모델 개발**

✅ **문제 정의**

- 사용자들이 **부분적으로 선택한 아이템이 있을 때, 어떤 아이템을 추가해야 할지 추천하는 모델이 필요**
- 단순 인기 아이템 추천이 아닌, **실제 코디 패턴을 학습할 수 있는 모델 필요**
- 단순 추천 모델 뿐만 아니라 정답이 **상위 랭크에 포함되도록 하는 랭킹 모델**도 고려해 구현 필요

✅ **해결 방법**

- 패턴 분석을 위해 벡터 표현 필요 → One-Hot Encoding을 활용해 데이터를 변환함
- 조건부 패턴 분석에 효과적인 **Apriori Algorithm(Association Rule Mining)을 활용해 연관 규칙을 학습함**
    - **함께 자주 등장하는 아이템 조합을 분석**하여 누락된 아이템 예측
    - Support(지지도), Confidence(신뢰도), Lift(향상도) 기반으로 가장 적절한 아이템 추천
- **가장 적절한 누락된 아이템 추천**
    - 주어진 아이템 조합이 **생성된 연관 규칙의 선행 항목(Antedecent)에 포함되는지 확인**
    - 포함될 경우, **후행 항목(Consequent)에서 추천 아이템을 후보로 선정**
- Apriori Algorithm을 통해 예측된 **100개의 후보 아이템을 랭킹하여 최종 추천 리스트 생성**
    
    

✅ **성과**

- **Accuracy 0.101 달성 (랜덤 추천 대비 100배 높은 성능 기록)**
- 평균 Rank 93.787 달성 **(랜덤 추천 대비 7% 성능 향상)**

---

## 👩‍🔧Team

2인 팀 프로젝트 (KAIST AI506: Data Mining and Search 수업)

---

## **💪 Remark**

✅ **그래프와 Node2Vec을 활용한 패션 추천 시스템 설계 및 최적화**

✅ **Apriori Algorithm을 적용하여 불완전한 코디 자동 완성 구현**

---

![image](https://github.com/user-attachments/assets/96cdc0d7-4ad9-487a-a63f-82ae9ddfede7)
![image](https://github.com/user-attachments/assets/3e70528d-ccb6-45bb-99c6-c3743b912378)

