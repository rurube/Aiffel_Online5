# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 손정민
- 리뷰어 : 본인의 이름을 작성하세요.


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [v] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  
- [v] 주석을 보고 작성자의 코드가 이해되었나요?

코드 상단과 옆, 아래에 주석이 자세하게 기록되었습니다.


```python
# (1)데이터 가져오기
from sklearn.datasets import load_diabetes
diabetes=load_diabetes() # diabetes 데이터 가져오기
df_X = diabetes.data # diabetes.data df_X에 저장
df_y = diabetes.target # diabetes.target df_y에 저장
print(df_X.shape)
print(df_y.shape)
```

- [v] 코드가 에러를 유발할 가능성이 없나요?

코드에 에러가 없습니다.

- [v] 코드 작성자가 코드를 제대로 이해하고 작성했나요?

바플롯과 히트맵을 이용한 추가적인 분석을 볼 때,
데이터를 가져오면서부터 시각화에 이를 때까지 흐름을 잘 이해하고 있는 것으로 판단됩니다.

```python
# (4) X, y 컬럼 선택 및 train/test 데이터 분리
#sns.barplot(x='year', data=train, y='count') #사용
#sns.barplot(data = train, x = 'month', y = 'count') #사용
sns.barplot(data = train, x = 'day', y = 'count') #제거
#sns.barplot(data = train, x = 'hour', y = 'count') #사용
#sns.barplot(data = train, x = 'season', y = 'count') #사용
#sns.pointplot(data = train, x = 'hour', y = 'count', hue='workingday') #사용
#sns.pointplot(data = train, x = 'hour', y = 'count', hue='holiday') #사용
#sns.pointplot(data = train, x = 'hour', y = 'count', hue='weather') #사용

data = train[['year', 'month', 'hour', 'season', 'workingday', 'holiday', 'weather', 'temp', 'atemp', 'humidity', 'windspeed']]
colormap = plt.cm.PuBu
sns.heatmap(data.corr(),annot=True, cmap=colormap) # 변수끼리 상관관계가 너무 높은 [month/season], [temp/atemp] 중 month, temp만 사용
```

- [v] 코드가 간결한가요?

네, 간결합니다.
흐름이 간결하고, 추가적인 내용은 주석으로 설명되고 있습니다.


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

제 수준에서는 개선할 곳이 보이지 않습니다.

```python
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
