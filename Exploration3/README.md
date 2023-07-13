# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 손정민
- 리뷰어 : 홍서이


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [O] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 이미지, 모델을 불러오는 과정에서 주소가 달라서 오류가 발생하였는데 이를 해결하니 정상적으롤 작동하였습니다. **상대 경로**를 사용하거나 docker 같은 가상화 컨테이너를 사용하여 이러한 문제를 해결할 수 있다고 합니다.

- [O] 주석을 보고 작성자의 코드가 이해되었나요?
  > 코드들을 함수화였고 해당 함수에 대한 주석이 포함되어 있어서 깔끔하고 이해하기 쉬웠습니다!

  ```python
  def set_sticker(sticker, dlib_rects, list_landmarks): # 스티커 적용 위치 설정 함수
    for dlib_rect, landmark in zip(dlib_rects, list_landmarks):
        x = landmark[30][0]
        y = landmark[30][1] + 8
        w = h = dlib_rect.width() # 중심점 정하고

    img_sticker = cv2.resize(sticker, (w,h))

    refined_x = (x - w // 2) # 스티가 중심에 올 수 있도록 설정
    refined_y = y - h // 2 
        
    return refined_x, refined_y, img_sticker
  ```

- [-] 코드가 에러를 유발할 가능성이 없나요?
  > 파일 경로 문제 때문에 오류가 발생할 가능성이 있습니다. [상대경로](https://wikidocs.net/153154)를 사용하면 이러한 문제를 해결할 수 있을 것 같습니다.

 
- [O] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 코드를 제대로 이해하고 작성하였으며 기존 내용을 활용한 새로운 코드도 작성하여 주어진 문제를 해결하였습니다.
  
  ```python
    import math

  def rotate_sticker(sticker, list_landmarks): # 스티커 돌리기 함수
      for landmark in list_landmarks:
          tan_theta = (landmark[30][0]-landmark[27][0])/(landmark[30][1] - landmark[27][1]) # 일직선인 점 30번과 27번 이용
          theta = np.arctan(tan_theta) # arctan 이용하여 각도 알아내고
          rotate_angle = theta * 180/math.pi # 이용할 수 있는 각도로 변환
    
      sticker_center = tuple(np.array(sticker.shape[1::-1]) / 2)
      rot_mat = cv2.getRotationMatrix2D(sticker_center, rotate_angle, 1.0) # 사진 회전
      result = cv2.warpAffine(sticker, rot_mat, sticker.shape[1::-1], flags = cv2.INTER_LINEAR, borderValue=(255,255,255))

      return result
  ```
  
- [O] 코드가 간결한가요?
  > 코드들을 함수형으로 작성하여 재사용이 가능하게 하였습니다. 그리고 작성한 함수들을 기반으로 다른 이미지에 대해서 동일한 작업을 진행할 시 간결한 코드만으로 작업을 수행할 수 있도록 하였습니다.

  ```python
  img_rgb, img_show = load_image('jaemindark.jpeg')
  sticker(img_show, img_rgb, 'cat.png')
  show_image(img_rgb)
  ```



# 참고 링크 및 코드 개선
```python
def load_image(name): # 이미지 로드 함수
    image_dir = os.getenv('HOME')+'/aiffel/review/Aiffel_Online5/Exploration3/images/'
    my_image_path = join(image_dir, name)
    img_bgr = cv2.imread(my_image_path)
    img_rgb = cv2.cvtColor(img_bgr, cv2.COLOR_BGR2RGB) # rgb로 변환한 원본
    img_show = img_rgb.copy() # rgb 변환한 copy본

    return img_rgb, img_show
```

해당 코드를 상대경로를 이용하여 수정할 수 있습니다.

```python
def load_image(name):
    image_dir = './images/' # 상대경로로 주소 변경
    my_image_path = join(image_dir, name)
    img_bgr = cv2.imread(my_image_path)
    img_rgb = cv2.cvtColor(img_bgr, cv2.COLOR_BGR2RGB) 
    img_show = img_rgb.copy()

    return img_rgb, img_show
```
