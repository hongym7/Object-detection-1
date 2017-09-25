# CNN

Multi-layered NN 을 비전에 적용할 때의 문제점 -> http://laonple.blog.me/220587920012 

글자의 topology 는 고려하지 않고, 말 그대로 raw data 에 대해서 직접 처리하기 때문에 엄청나게 학습 데이터가 많이 필요하게 되고, 
또한 거기에 따른 학습 시간을 대가로 치뤄야 한다는 점.

결과적으로 기존의 fully-connected multi-layered NN 를 사용하면, 다음과 같은 3가지 측면에서 문제가 발생함.
1. 학습 시간
2. 네트웍의 크기
3. 변수의 개수

영상 처리 분야에서 convolution 은 주로 filter 연산에 사용이 되며, 
영상으로부터 특정 Feature 들을 추출하기 위한 필터를 구현할 때 convolution 을 사용한다.

CNN 은 multi-layered NN 에 비해 다음과 같은 중요한 특징을 갖는다.

1. Locality (local connectivity): 
CNN 은 local 정보를 활용한다. 
공간적으로 인접한 신호들에 대한 correlation 관계를 비선형 필터를 적용하여 추출해 낸다. 
이런 필터를 여러 개 적용하면 다양한 local 특징을 추출해 낼 수 있게 된다. 
max-pooling 방식의 sub-sampling 과정을 거치면서 영상의 크기를 줄이고 local feature 들에 대한 filter 연산을 반복적으로 적용하면 
점차 global feature 를 얻을 수 있게 된다.

2. Shared Weight:
Convolution 의 개념을 설명할 때 보았던 것처럼, 동일한 개수를 갖는 filter 를 전체 영상에 반복적으로 적용함으로써 
변수의 수를 획기적으로 줄일 수 있으며, topology 변화에 무관한 항상성 (invariance) 를 얻을 수 있게 된다.

CNN 의 과정은 다음과 같다.
Input -> Feature extraction (filter) -> Shift and distortion invariance (sub-sampling) -> Classification -> Output (edited)

즉,
1. 특징을 추출하기 위한 단계
2. topology 변화에 영향을 받지 않도록 해주는 단계
3. 분류기 단계

이동이나 변형 등에 무관한 학습 결과를 보이려면, 좀 더 강하고 global 한 특징을 추출해야 하는데, 
이를 위해 통상적으로 (convolution + sub-sampling) 과정을 여러 번 거쳐 좀 더 전체 이미지를 대표하는 global 한 특징을 얻을 수 있다.
