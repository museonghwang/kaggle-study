# Statoil/C-CORE Iceberg Classfier Challenge

![statoil](/Statoil%20C-CORE%20Iceberg%20Classifier%20Challenge/image/statoil.png)

https://www.kaggle.com/c/statoil-iceberg-classifier-challenge

## Description

캐나다 동쪽 해안에서는 표류하는 빙하가 자칫 위험이 될 수 있다고 합니다. 그래서 많은 연구기관, 기업들이 이 위험을 피할 방법을 찾기 위해 노력하고 있다고 하네요. 위성사진을 이용해 지속적으로 모니터링을 한다고 합니다. Statoil 이라는 국제 에너지 기업과 C-CORE 라는 위성 기업이 이 컴퍼티션을 주최하였는데, 이들이 제공한 위성사진을 가지고 배(ship)와 빙하(iceberg)를 잘 구분해내는 머신러닝, 딥러닝 모델을 세우는 게 목표입니다.

데이터의 속성(feature)는 `band_1`, `band_2`, `inc_angle` 로 단 3가지입니다. `band_1`과 `band_2` column은 한 element 당 75x75 = 5,625개의 float값으로 구성되어 있습니다. 이는 75x75의 pixel값으로 이미지 데이터라고 보시면 되겠습니다. 

본 대회의 주요 커널에서는 대부분 딥러닝 CNN(합성곱 신경망)을 활용하여 결과를 예측했습니다.


## 1st Kernel: Keras Model for Beginners (0.210 on LB)+EDA+R&D

해당 커널에서는 가장 기본적인 합성곱 신경망(Convolutional Neural Network, CNN)을 적용하여 결과를 예측했습니다. 특히 간단한 전처리 만으로 학습을 진행했고, 학습전 plotly를 사용하여 빙하와 배의 이미지 특성차이를 3D로 시각화 하였습니다.

![iceberg](/Statoil%20C-CORE%20Iceberg%20Classifier%20Challenge/image/iceberg.png)
![ship](/Statoil%20C-CORE%20Iceberg%20Classifier%20Challenge/image/ship.png)

CNN의 기초에 대해 배울 수 있는 좋은 커널이었으며, 프레임워크는 Keras를 사용했습니다.


## 2nd Kernel: Convolutional Neural Net Tutorial (tensorflow)

2번째 커널인 Convolutional Neural Net Tutoriald은 다양한 Image Augmentation을 사용하여 Train Data를 증강시킵니다. 

* Image Rotation
* Horizontal translation
* Vertical translation
* Translation along positive diagonal
* Translation along negative diagonal
* Flip Image
* Zoom image

대표적으로 위와같은 Augmentation을 적용하며 각도의 방향 및 기타 파라미터를 수정 및 적용하여 1103개의 Train data를 16545개로 증강시킵니다.

![iceaug](/Statoil%20C-CORE%20Iceberg%20Classifier%20Challenge/image/iceaug.png)

<br>

1st Kernel: https://www.kaggle.com/code/devm2024/keras-model-for-beginners-0-210-on-lb-eda-r-d/notebook

2nd Kernel: https://www.kaggle.com/code/itratrahman/convolutional-neural-net-tutorial-tensorflow/notebook