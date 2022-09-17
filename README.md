# ImageClassification

기계학습과 딥러닝으로 이미지 분류기 만들기 프로젝트

<details>
<summary>기계학습을 활용한 풍경 이미지 분류</summary>


## Problem 3
train_dataset의 image_name열에는 각 이미지의 파일명이 담겨있다.
파일명을 참조해 image를 하나씩 열어 array로 만든 뒤, X_train 리스트에 append.
모든 이미지 array가 리스트에 담긴 후에 np.array(X_train)으로 X_train을 array로 바꿔줬다.

## Problem 6
shift_image로 x방면으로 1~3픽셀, y방면으로 1~3픽셀 움직인 것과
horizontal_flip으로 X축으로 뒤집은 것을 train set에 추가.
X_train보다 X_train_augmented가 3배 더 크다.

## Problem 7
가장 좋은 하이퍼파라미터 조합을 찾기 위해 k는 7부터 19 사이의 홀수, 거리는 L1 or L2로 놓고 모든 경우에 대해 모델을 학습시켰다. best_acc에 가장 높았던 검증 결과를 담고 best_parameter에 그 검증 결과를 나오게 한 파라미터를 담았다.
결과는 k=17, 거리=L1이었으나 혼동행렬을 보니 label 0을 잘 분류하지 못 했다.
L2를 쓰는 것이 L1보다 정확도는 다소 떨어질지 몰라도 라벨간 오류의 차이가 적은 양상을 보였다.

## Problem 8
100 종류의 스포츠 사진 데이터셋과
https://www.kaggle.com/datasets/gpiosenka/sports-classification
고양이와 강아지 사진 데이터셋을 썼다.
https://www.kaggle.com/datasets/tongpython/cat-and-dog

모델은 LogisticRegression을 썼다.

스포츠 사진 데이터셋은 100 class를 모두 학습시키면 정확도가 약 28%였다.
train set을 뽑을 때 10 class만 뽑아 학습시키면 가장 좋은 정확도가 68%.
검증 데이터셋의 숫자가 적기 때문에 가장 좋은 모델인지는 모르겠다.

</details>

<details>
<summary>CNN을 활용한 이미지 분류</summary>


## Problem 3 
레이어를 만드는 건 어렵지 않았으나 입력 텐서 크기와 출력 텐서 크기를 맞추는 게 어려웠다.
특히 Max Pooling 이후 크기가 어떻게 되는 건지 모르겠다.

## Problem 7
torch에 내장된 Pre-trained 된 ResNet50을 불러와 전이학습시켰다.
epoch는 100 이상. mix-up을 사용했다.
최종적인 결과는 94.04%였다. 학습된 파라미터는 Mymodel2_new.pt에 저장되어 있다.

</details>