# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 손정민
- 리뷰어 : 홍서이


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [O] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 정상적으로 동작하며 목표 성능인 RMSE 11000이하를 달성하였습니다.
- [O] 주석을 보고 작성자의 코드가 이해되었나요?
  > 셀마다 주석을 달아주시고 코드도 깔끔하게 작성해주셔서 쉽게 이해할 수 있었습니다! 공부하는데 참고할 수 있을 것 같아요
- [O] 코드가 에러를 유발할 가능성이 없나요?
  > 없는 것으로 보입니다
- [O] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 네. EDA를 통해 데이터를 적절히 탐색하였고 그리드 서치를 이용해서 각 모델간 최적의 하이퍼파라미터를 탐색하고 이를 기반으로 가장 높은 성능을 가진 모델 2개를 average blending하여 좋은 score를 얻었습니다.
- [O] 코드가 간결한가요?
  > 코드가 간결하고 깔끔하게 작성되었습니다.

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

개선사항이 없어 보입니다!

```python
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
