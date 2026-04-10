# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 황성연
- 리뷰어 : 정주열

# PRT(Peer Review Template)
- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
        - 영화 시놉시스 코퍼스 데이터를 기반으로 단어 임베딩(Word Embedding) 알고리즘을 구축하고, 특정 대상(Target)과 속성(Attribute) 장르 간에 내재된 의미적 편향성을 WEAT 스코어를 통해 정량적으로 측정 및 시각화하였음.
    <img width="364" height="362" alt="image" src="https://github.com/user-attachments/assets/ecd2bbf8-7e97-42e6-9085-094d7aee15e5" />
    <img width="802" height="846" alt="image" src="https://github.com/user-attachments/assets/d794b838-9d9e-456c-9b9e-b0e3074401c6" />

- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭을 왜 핵심적이라고 생각하는지 확인
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    - 해당 코드의 기능, 존재 이유, 작동 원리 등을 기술했는지 확인
    - 주석을 보고 코드 이해가 잘 되었는지 확인
        - 임베딩 모델 학습시키는 코드에서 하이퍼 파라미터가 설명되어 있어서 이해가 잘되었음.
    <img width="745" height="422" alt="image" src="https://github.com/user-attachments/assets/b59576b2-bd01-44dd-ab6c-2860f55c4487" />

- [x]  **3. 에러가 난 부분을 디버깅하여 문제를 해결한 기록을 남겼거나
새로운 시도 또는 추가 실험을 수행해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인
    - 프로젝트 평가 기준에 더해 추가적으로 수행한 나만의 시도, 
    실험이 기록되어 있는지 확인
        - 단순 교집합 폐기 방법을 시도해봤는데 성능이 안좋은 것을 파악하고, Margin Filtering이라는 새로운 방식으로 편향성 체크를 함. 문제 원인과 해결과정이 잘 기록되어있고, 결과 분석도 잘되어 있음.
    <img width="776" height="533" alt="image" src="https://github.com/user-attachments/assets/a1c5fc4b-0a32-48e4-b281-2ed2415d88cd" />

- [x]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해
    배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
    - 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
        - 프로젝트 회고 부분이 잘 작성되어 있고, 진행한 내용에 대한 이해, 새로운 알고리즘 설계, 결과 분석까지 다시 한번 체계적으로 정리되어 있음.
    <img width="781" height="360" alt="image" src="https://github.com/user-attachments/assets/5d49b06c-62ef-4551-8832-2f58885f479e" />

- [x]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화/모듈화했는지 확인
        - 아래 그림처럼 코사인 유사도, 편향성 차이 구하기, WEAT score 도출하는 함수로 나눠서 기능별로 모듈화가 잘되어 있어서 코드 읽기가 편했음.
    <img width="773" height="426" alt="image" src="https://github.com/user-attachments/assets/3409e90c-42fe-4faf-a7fa-9ab376565405" />


# 회고(참고 링크 및 코드 개선)
전반적으로 코드가 가독성이 좋아서 읽기 너무 편했습니다. STEP1부터 STEP4까지 이어지는 흐름이 자연스러워서 저도 배웠던 내용을 복습하는 느낌으로 봐서 너무 좋았습니다. 특히 STEP3에서 교집합 폐기와 새로운 아이디어를 제안해서 결과를 도출하고 비교한 내용이 정말 좋았던 것 같습니다. 

