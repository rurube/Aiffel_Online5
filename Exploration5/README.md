# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 손정민
- 리뷰어 : 박혜원


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [O] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 인아웃포커싱 효과가 적용된 인물모드 사진과 동물 사진, 배경전환 크로마키사진를 성공적으로 제작하였습니다.
  > 제작한 인물모드 사진들에서 나타나는 문제점을 정확히 지적하였다.	인물사진에서 발생한 문제점을 정확히 지적한 사진을 제출하였습니다. 
  > semantic segmentation mask의 오류를 보완할 수 있는 좋은 솔루션을 이유와 함께 제시하였습니다. 
- [O] 주석을 보고 작성자의 코드가 이해되었나요?
  > 주석이 이해 되도록 간결하게 잘 쓰여져 있어서 이해가 잘 되었습니다.
- [O] 코드가 에러를 유발할 가능성이 없나요?
  > 네 이미지 및 모델 관련 위치만 환경에 맞게 수정한담에러 유발할 가능성은 없어 보입니다.
- [O] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 네. 주석 및 Step, 그리고 최종적으로 문제점 분석까지 전체 흐름 및 과정을 잘 이해하며 작성한 것을 확인 할 수 있었습니다.
- [O] 코드가 간결 한가요?
  > 코드가 단락별로 잘 분리되어 있으며 모든 과정을 함수화 하여 간결하게 작성해주셨습니다. 


# 참고 링크 및 코드 개선
```python
수정되어야한다고 느낀 부분은 크게 없었으나 굳이 꼽아야한다면,

image_segmentation 함수에서 
- model_file, model_dir, model_url도 인자로 받게 하고, 
- model_url 변수를 사용하여, 해당 디렉토리에 model 이 있으면 가져다쓰고, 없으면 url 을 통해서 모델을 다운받는 식으로 함수를 정돈하면 좋을 것 같습니다. 

import os
import urllib.request

def image_segmentation(my_image_path, model_file, model_dir, model_url):
    model_file_path = os.path.join(model_dir, model_file)
   

    # Check if the model file exists in the model_dir
    if not os.path.exists(model_file_path):
        # If the model file doesn't exist, download it from model_url
        print(f"Downloading the model file from {model_url}...")
        urllib.request.urlretrieve(model_url, model_file_path)
        print("Model file downloaded successfully.")

    model = semantic_segmentation()
    model.load_pascalvoc_model(model_file_path)
    segvalues, output = model.segmentAsPascalvoc(my_image_path)

    return segvalues, output
```
