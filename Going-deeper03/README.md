# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 손정민
- 리뷰어 : 김민식


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [O] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  
- [O] 주석을 보고 작성자의 코드가 이해되었나요?
  > 코드에 직접적인 주석도 있지만 각 과정을 markdown으로 잘 구분해 주셔서 과정을 이해하기 쉬웠습니다.
- [O] 코드가 에러를 유발할 가능성이 없나요?
  > 각 셀마다 수행결과를 표시해 주셔서 에러가 없음을 확인하였습니다.
- [O] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 각 과정을 잘 수행하셨고, 고찰과 회고를 통해 전체적인 과정에 대해 생각해보신 점이 코드를 잘 이해했다고 생각합니다.
- [O] 코드가 간결한가요?
  > 각 과정에 대해 필요한 부분만 코드를 작성해주셨습니다.

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.
```python
  ## 코드 부분 주석 예시
  m1 = X[0].tocoo()   # art를 TF-IDF로 표현한 sparse matrix를 가져옵니다. 
  m2 = X[1].tocoo()   # gen을 TF-IDF로 표현한 sparse matrix를 가져옵니다. 

  w1 = [[i, j] for i, j in zip(m1.col, m1.data)]
  w2 = [[i, j] for i, j in zip(m2.col, m2.data)]

  w1.sort(key=lambda x: x[1], reverse=True)   #art를 구성하는 단어들을 TF-IDF가 높은 순으로 정렬합니다. 
  w2.sort(key=lambda x: x[1], reverse=True)   #gen을 구성하는 단어들을 TF-IDF가 높은 순으로 정렬합니다. 
  ```

# 참고 링크 및 코드 개선

