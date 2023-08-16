# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 손정민
- 리뷰어 : 김성진


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [v] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  - 시간상 직접 실행시켜보지는 않았지만, 코드대로라면 문제를 해결하였습니다.
- [v] 주석을 보고 작성자의 코드가 이해되었나요?
  - 네, 섹션별로 나뉘어있어 잘 이해가 되었습니다. 
- [v] 코드가 에러를 유발할 가능성이 없나요?
  - 네, 없습니다.
- [v] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  - 네, 코드 흐름상 잘 이해하고 작성되었습니다.
- [v] 코드가 간결한가요?
  - 네, 간결합니다.

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.


- 코드 예: SentencePiece Tokenize 함수
```python
def sp_tokenize(s, corpus): 

    tensor = []

    for sen in corpus:
        tensor.append(s.EncodeAsIds(sen))

    with open("./korean_spm.vocab", 'r') as f:
        vocab = f.readlines()

    word_index = {}
    index_word = {}

    for idx, line in enumerate(vocab):
        word = line.split("\t")[0]

        word_index.update({word:idx})
        index_word.update({idx:word})

    tensor = tf.keras.preprocessing.sequence.pad_sequences(tensor, padding='post')

    return tensor, word_index, index_word
```

- 성능 개선하기

### SentencePiece 성능 개선하기
다른 조건은 위의 SentencePiece 과정과 동일하나, LSTM 모델을 양방향 LSTM으로 변경하였다.

```python
word_vector_dim = 16

model3 = keras.Sequential([
    keras.layers.Embedding(vocab_size, word_vector_dim, input_shape=(None,)),
    keras.layers.Bidirectional(keras.layers.LSTM(8)), # 양방향 LSTM 사용
    keras.layers.Dense(8, activation='relu'),
    keras.layers.Dense(1, activation='sigmoid')
])

model3.summary()
```

- 결과에 대한 고찰/회고 내용

### 고찰
|name|tokenizer|모델|test accuracy|
|:---:|:---:|:---:|:---:|
|splstm|SentencePiece|LSTM|0.8305|
|mecablstm|mecab|LSTM|0.6086|
|spbdlstm|SentencePiece|양방향 LSTM|**0.8418**|  

Tokenizer 부분에서는 KoNLPy mecab 형태소 분석기에 비해 SentencePiece가 같은 모델 기준 0.2정도 크게 증가하였다. SentencePiece 토크나이저로는 LSTM, 양방향 LSTM 두 모델을 훈련시켰는데 일반 LSTM에 비해 양방향 LSTM이 정확도가 0.01정도 높았다.  

### 회고
|kpt|내용|
|:---|:---|
|**Keep**|SentencePiece를 이용한 모델을 성공적으로 구현했다.|
|**Problem**|많은 조건에 대해 실험해보지 못했다.|
|**Try**|성능을 더 높일 수 있는 다른 조건(다른 모델, vocab size 등)에 대해 시도해본다.|


# 참고 링크 및 코드 개선

- 혹시나 나중에 FastText 모델을 사용하실 때 참고할만한 웹페이지 남겨놓겠습니다.
- [Link](https://frhyme.github.io/nlp/fasttext_pretrained_wiki/) : FastText, 학습된 모델과 벡터 가져와서 사용하기 : frhyme.code (github.io)
    - 사전학습된 모델 용량이 커서 메모리에 안 올라가더라고요.
    - 전 벡터로 불러와서 썼습니다.
- [Link](https://fasttext.cc/docs/en/crawl-vectors.html) : Word vectors for 157 languages · fastText (fasttext.cc) |
    - 한국어 사전학습 모델과 벡터 다운로드 페이지입니다.