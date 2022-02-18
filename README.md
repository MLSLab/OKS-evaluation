# OKS-evaluation




https://cocodataset.org/#download 에서 제공하는 2017 Train/Val annotations 를 사용한다.

예제 이미지를 한 개 선택한 후 bbox, keypoints를 이미지에 그려보고
simple-HRNet 으로 추출한 예측값을 사용해 OKS 를 계산해본다.


![image](https://user-images.githubusercontent.com/32845598/154606038-e2ef765d-4f39-4b16-84f2-ddac38a7bc38.png)
레이블에 있는 모든 keypoint ( v_i > 0 ) 에 대해 평균을 구한다.

레이블링 되어있지 않는 예측 keypoint 는 OKS 에 영향을 미치지 않는다.

ex ) 검출기가 왼쪽 손목의 keypoint 를 예측해서 결과가 나왔어도 왼쪽 손목이 레이블링 되어있지 않는다면 OKS 는 계산되지 않고 결과에 영향을 미치지 않는다.

예측이 완벽하면 OKS = 1, 정답과 예측의 사이가 작을 수록 OKS 값이 1에 가까워진다.

객체 scale  에 대한 keypoint 당 표준편차 
 를 보면  값은 keypoint 에 따라 크게 달라진다.

어깨, 무릎, 엉덩이 등이 머리에 있는 눈,코,귀보다 훨씬 큰 를 갖는 경향이 있다.
