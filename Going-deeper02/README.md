# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 손정민
- 리뷰어 : 김민식


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [O] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  
- [O] 주석을 보고 작성자의 코드가 이해되었나요?
  > 각 과정에 대해 명시가 잘 되어 있고, 모델 분석내역에 대한 정리도 잘 되어있어서 이해하기 좋았습니다.
  >> 모델 분석내역 관련내용에 대한 정리 &rarr; below from `고찰`
- [O] 코드가 에러를 유발할 가능성이 없나요?
  > 각 과정이 함수 등으로 잘 구분되어 있으며, 모듈 warning도 커버할 수 있도록 구성되었습니다.
  >> 예시 기준 `train_model()`, `warnings.filterwarnings("ignore")`
- [O] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 각 모델의 조건별 훈련결과를 잘 도출해내었으며, 최종적으로 표로 정리하여 `num_words` 케이스별로 잘 정리해주었습니다.
  >> `Table example` 에 table 표시함
- [O] 코드가 간결한가요?
  > `train_model()` 과 같이 함수화도 잘 되어있고, 각 과정 마다 분할을 잘 해두어 코드들이 간결하게 잘 표현되었습니다.

# 예시
```python
## ...
import warnings
warnings.filterwarnings("ignore")
## ...

def train_model(xtrain, ytrain, xtest, ytest):
    nb = MultinomialNB() # 나이브 베이즈 분류기
    cb = ComplementNB() # 컴플리먼트 나이브 베이즈 분류기
    lr = LogisticRegression(C=10000, penalty='l2', max_iter=3000) # 로지스틱 회귀
    lsvc = LinearSVC(C=1000, penalty='l1', max_iter=3000, dual=False) # 선형 서포트 벡터 머신
    tree = DecisionTreeClassifier(max_depth=10, random_state=0) # 결정 트리
    forest = RandomForestClassifier(n_estimators=5, random_state=0) # 랜덤 포레스트
    grbt = GradientBoostingClassifier(random_state=0) # 그래디언트 부스팅 트리
    voting_classifier = VotingClassifier(estimators=[ # 보팅
            ('lr', LogisticRegression(C=10000, penalty='l2', max_iter=3000)),
            ('cb', ComplementNB()),
            ('grbt', GradientBoostingClassifier(random_state=0))
    ], voting='soft', n_jobs=-1)

    model_list = [nb, cb, lr, lsvc, tree, forest, grbt, voting_classifier]

    for model in model_list:
        model.fit(xtrain, ytrain)
        pred = model.predict(xtest)
        print(f'{model} 모델 정확도: {accuracy_score(ytest, pred)}, f1-score: {f1_score(ytest, pred, average="weighted")}')
```

---

Table example

|모델/num_words|all|3000|5000|10000|15000|
|:---:|:---:|:---:|:---:|:---:|:---:|
|나이브 베이즈 분류기|0.600|**0.687**|0.673|0.657|0.633|
|컴플리먼트 나이브 베이즈 분류기|0.765|0.764|0.771|0.771|**0.772**|
|로지스틱 회귀|<span style="color:red">0.817</span>|0.788|0.804|0.810|0.814|
|선형 서포트 벡터 머신|0.788|0.756|0.777|0.785|**0.793**|
|결정 트리|0.621|**0.626**|0.618|0.620|0.619|
|랜덤 포레스트|0.654|0.685|**0.700**|0.674|0.671|
|그래디언트 부스팅 트리|0.771|**0.776**|0.768|0.769|0.770|
|보팅|**0.816**|0.803|0.810|**0.816**|0.815|

# 참고 링크 및 코드 개선
```python
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
