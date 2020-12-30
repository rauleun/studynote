* RGBD 

*** Segmentation

1. Additional to RGB image, depth channel can be treated as a channel for the input.

2. Encode depth into a three-dimensional HHA (horizontal disparity, height above ground, and angle with gravity) image.

3. Separately predict features for the two modalities (RGB and depth) and fusing for final predition.



*** Kinect camera

Microsoft에서 처음 개발된 kinect camera는 원래 Xbox360의 인터페이스 장비인데, depth와 skeleton 정보를 쉽게 얻을 수 있어서 많은 주목을 받았다.

크게 RGB camera의 color sensor, IR emitter과 IR Depth sensor 등으로 구성되어 있다.

적외선 카메라를 활용하여 빔 포인터의 각 픽셀간 거리를 측정하여 정면에 존재하는 사물의 깊이를 추출한다. (Time of Flight method) 

보통 color image와 depth image 간의 resolution 차이가 약간씩 존재하는 듯 하다. (kinect v1 기준 color image : 640x480, depth image : 320x240)

RGBD camera의 output은 RGB color image와 depth image의 두 가지로 존재하는데, depth image는 raw data(mm 단위의 절대적 거리를 나타냄)와 normalized data로 구별될 수 있다.

보통 게임과 연동되어서 많이 사용한다. (XBOX360 및 Nintendo Wii 등에서 사용자의 동작을 인식하는 게임에 활용)


*** ZED stereo camera

Steroe LABS에서 개발한 3D sensing camera.

기존의 camera와 달리 2개 이상의 렌즈를 활용하여 depth 정보를 추출한다.

Kinect camera와 유사하게 RGB color image에 depth image를 같이 제공한다.


** Dataset 

- Yonsei Univ CVLAB에서 제공하는 RGB+D Dataset

Kinect v2 및 ZED stereo camera로부터 RGB-D frame을 추출한다.

Depth filled, depth raw, depth v (normalized), color의 네 가지로 구성된다. 

https://dimlrgbd.github.io/



- Washington Univ에서 제공하는 RGB-D Dataset

Object와 Scene Dataset으로 분류되어 있고 각각 300개 이상의 물체와 22개 이상의 풍경을 담을 video sequence로 구성되어 있다.

같은 크기(640x480)의 RGB image(3 channels)와 depth image(1 channel)로 구성되어 있다.

https://rgbd-dataset.cs.washington.edu/index.html


- NYU-D V2

Indoor scene에 대한 video sequence 영상을 제공하며, Microsoft Kinect camera로 퐐영되었다.

Instance 별로 numbering이 되어 있어서 Instance segmentation에도 활용 가능하다.

Segmentation task에 대한 benchmark dataset으로 활용된다.

https://cs.nyu.edu/~silberman/datasets/nyu_depth_v2.html

- SUN RGB-D

All major scene understanding task에 대해 RGB-D Benchmark dataset르으로 활용된다.
