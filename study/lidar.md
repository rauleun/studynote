*LiDAR*

*** LAS file format***

현업에서 가장 보편적으로 활용되는 LiDAR data format으로, lidar point cloud data를 저장하기 위해 고안되었다.

Public header block, Variable length records, Point data records, Extended variable length records 의 네 가지로 구성되어 있다.

그 중 Point data records는 각 point에 대한 좌표값이나 클래스 정보 등을 저장하고 있다. 


***Principle***

- Time of Flight (TOF)

Laser pulse를 방출하고, 측정 범위 내의 물체에 반사되어 수신될 대 까지의 시간을 측정하여 거리를 계산합니다.

- Phase Shift

특정 주파수를 가지고 진동하는 sinosoidal Laser pulse를 방출하고, 반사되어 오는 Laser pulse와의 phase difference를 측정하여 거리를 계산합니다.

- Wavelength

주로 905nm 또는 1550nm의 파장 대역을 활용합니다. 1550nm LiDAR가 noise에 더 robust하고 안전하지만, 전력사용량이 더 많고 가격이 비쌉니다.



