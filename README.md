# Personalized_outfit_recommendation_and_generation
Recommendation &amp; Ranking, Node2Vec, Association Rule Mining (Apriori algorithm)

## **📑 Summary**

**"오늘 뭐 입지?"**

온라인 쇼핑 사용자들은 수많은 아이템 중에서 자신에게 어울리는 스타일을 찾는 데 어려움을 겪습니다. 이 고민을 해결하기 위해, **사용자 맞춤형 패션 추천 시스템**을 개발하는 프로젝트를 진행했습니다.

사용자가 클릭한 패션 아이템 데이터를 활용해 **개인화된 코디를 추천**하고, 불완전한 코디에서 **누락된 아이템을 자동으로 완성하는 AI 모델**을 구축했습니다. 특히, **Node2Vec을 활용한 그래프 기반 추천 모델과 Apriori 알고리즘을 적용하여 추천 정확도를 향상**시켰으며, 기존 방식보다 **더 정교한 스타일 추천이 가능하도록 개선**했습니다.

---

## **⭐ Contribution**

✅ **사용자-코디 관계를 효율적으로 모델링하기 위해 이분 그래프(Bipartite Graph) 생성.**

✅ **Node2Vec 알고리즘을 적용하여 각 노드를 128차원 벡터로 임베딩, 유사한 사용자 및 아이템 탐색을 최적화.**

✅ **불완전한 코디 보완을 위해 Apriori Algorithm을 활용한 연관 규칙 학습 진행 → Support, Confidence, Lift를 기반으로 자주 등장하는 아이템 조합 분석.**

✅ **반복 실험을 통해 최적의 Threshold(20%)를 설정하여 추천 모델 성능 개선.**

✅ **누락된 아이템 후보 100개를 랭킹하여 최종 추천 리스트 생성.**

✅ **Node2Vec 기반 추천 모델 Accuracy 0.702 달성 (기존 협업 필터링 대비 성능 향상).**

✅ **Apriori 기반 코디 완성 모델 Accuracy 0.101 기록 (랜덤 추천 대비 100배 높은 성능).**

---

### 👩‍🔧Team

2인 팀 프로젝트 (KAIST AI506: Data Mining and Search 수업)
---

![image](https://github.com/user-attachments/assets/96cdc0d7-4ad9-487a-a63f-82ae9ddfede7)
![image](https://github.com/user-attachments/assets/3e70528d-ccb6-45bb-99c6-c3743b912378)

