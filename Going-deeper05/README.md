# AIFFEL Campus Online 5th Code Peer Review
- 코더 : 손정민
- 리뷰어 : 최철웅


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  - 주어진 조건에 맞춰 텍스트 전처리 함수를 선언하였다.
  - 학습한 Transformer가 완벽한 번역문은 내보내진 못했으나 문장의 어법이 맞고 필요한 단어가 모두 들어있었다.
  - obama, cities, coffee와 같은 명사들이 본래 뜻과 높은 유사도를 이루는 모습을 확인하였다.
- [x] 주석을 보고 작성자의 코드가 이해되었나요?
  - preprocess_sentence 함수에서 전처리의 각 과정을 설명하였다.
  - positional_encoding 함수의 각 파라미터가 어떤 값이 들어가는지 설명하였다.
- [x] 코드가 에러를 유발할 가능성이 없나요?
  - MultiHeadAttention의 멤버 함수들의 연산이 각 텐서의 크기에 잘 맞춰서 작성하였다.
  - 실행결과 에러는 발생하지 않았다.
- [x] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  - 주석에 담긴 코드의 설명과 코드의 동작이 일치하였다.
- [x] 코드가 간결한가요?
  - 불필요하게 반복 작성한 코드는 없었다.
  - 모델 평가시 반복문을 통해 여러 문장의 번역 결과와 어텐션 점수를 한번에 보여주었다.

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.
```python
# 사칙 연산 계산기
class calculator:
    # 예) init의 역할과 각 매서드의 의미를 서술
    def __init__(self, first, second):
        self.first = first
        self.second = second
    
    # 예) 덧셈과 연산 작동 방식에 대한 서술
    def add(self):
        result = self.first + self.second
        return result

a = float(input('첫번째 값을 입력하세요.')) 
b = float(input('두번째 값을 입력하세요.')) 
c = calculator(a, b)
print('덧셈', c.add()) 
```

# 참고 링크 및 코드 개선
```python
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
