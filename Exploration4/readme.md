# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 손정민
- 리뷰어 : 이효겸


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 모델3개 이상, word2vec와의 분석, 정확도85%이상을 달성하여 문제를 잘 해결했습니다.
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 주석이 이해 되도록 간결하게 잘 쓰여져 있어서 이해가 잘 되었습니다.
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 데이터와 모델의 위치만 잘 확인 한다면 에러 유발할 가능성은 거의 없어 보입니다.
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 모델 개발 흐름에 따라 코드를 작성하였으며 
  > 모델 3개의 준비를 하나의 단락으로 훈련 단락을 따로 만든 것으로 보아 코드를 이해하지 못하면 작성하지 못할 코드로 보입니다.
- [X] 코드가 간결 한가요?
  > 코드가 단락별로 잘 분리되어 있으며 중복방지를 위한 함수 사용으로 간결한 코드를 추구한 것이 잘 보였습니다.
```python
def show_loss_acc(history_model, show): # epoch에 따라 증감하는 accuracy, loss 시각화
    history_dict = history_model.history
    acc = history_dict['accuracy']
    val_acc = history_dict['val_accuracy']
    loss = history_dict['loss']
    val_loss = history_dict['val_loss']
    
    epochs = range(1, len(acc) + 1)
    
    if show == 'acc':
        plt.plot(epochs, acc, 'bo', label='Training acc')
        plt.plot(epochs, val_acc, 'b', label='Validation acc')
        plt.title('Training and validation acc')
        plt.xlabel('Epochs')
        plt.ylabel('Acc')
        plt.legend()
    else:
        plt.plot(epochs, loss, 'bo', label='Training loss')
        plt.plot(epochs, val_loss, 'b', label='Validation loss')
        plt.title('Training and validation loss')
        plt.xlabel('Epochs')
        plt.ylabel('Loss')
        plt.legend()
    
    plt.show()
```

# 참고 링크 및 코드 개선
```python
굳이 꼽아 보자면 코드 사이간에 주석이 있었으면 더 좋았을것 같습니다.
이 코드를 보고 자신의 그래프 중복 코드나 변수명에 대해 좀 더 잘 적어야 겠다는 생각이 들었습니다.
```