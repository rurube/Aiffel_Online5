# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 손정민
- 리뷰어 : 김연수


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 네, 모두 정상적으로 동작하며, 주어진 과제를 해결했습니다.
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 네, 각 step에 대한 markdown과 주석이 잘 적혀있어, 전체적인 코드를 이해하는 데에 도움이 되었습니다.
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 모두 정상적으로 동작하는 것으로 보아, 에러를 유발할 코드는 없어 보입니다.
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 네, 과제에서 요구한 조건 뿐만 아니라 다양한 실험을 해본 것으로 보아, 코드 전체에 대한 이해를 바탕으로 작성된 것 같습니다.
- [X] 코드가 간결한가요?
  > 네, 간결합니다.

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.
### 1) Epochs 수를 다양하게 돌려보고 시각화했으며, 결과에 대해 분석했습니다.
```python
EPOCHS = 500 #10, 100, 500 

generator = UNetGenerator()
discriminator = Discriminator()
history = {'gen_loss':[], 'l1_loss':[], 'disc_loss':[]}

for epoch in range(1, EPOCHS+1):
    for i, (sketch, colored) in enumerate(train_images):
        g_loss, l1_loss, d_loss = train_step(sketch, colored)
        history['gen_loss'].append(g_loss)
        history['l1_loss'].append(l1_loss)
        history['disc_loss'].append(d_loss)      
            
            
        # 손실 출력
        if (i+1) % 200 == 0:
            print(f"EPOCH[{epoch}] - STEP[{i+1}] \
                    \nGenerator_loss:{g_loss.numpy():.4f} \
                    \nL1_loss:{l1_loss.numpy():.4f} \
                    \nDiscriminator_loss:{d_loss.numpy():.4f}", end="\n\n")
```
### 2) 회고 및 고찰이 굉장히 자세하게 이루어졌습니다.
결과물이 시각적으로 보이는 프로젝트였기 때문에 진행하면서 재미있었다. 구조적으로 완벽히 파악하지는 못했지만 관련 자료를 찾아보면서 수행하고 나니 전체적인 흐름에 대해 어느 정도는 알 수 있게 된 것 같다.
epoch 당 실행 시간이 길어 걱정했지만 목표한 10, 100, 500번을 모두 돌려볼 수 있어 다행이었다. 생각했던 것만큼 좋은 결과가 나오지 않았던 것에 대해서는 코드를 점검하고, 전처리나 모델에 대해 알아보면서 해결 방법을 찾아봐야겠다.
Image-to-Image Demo 사이트는 edges2cats, facades, edges2shoes, edges2handbags를 제공하는데, 각각 고양이, 건물, 신발, 핸드백 이미지를 pix2pix로 학습시킨 것으로 직접 그림을 그려넣으면 변환해준다. (재미있으므로) 해보고, 직접 구현에도 도전해볼 수 있을 것 같다.

# 참고 링크 및 코드 개선
```python
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
