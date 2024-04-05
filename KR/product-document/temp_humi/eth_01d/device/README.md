# 디바이스 연결 방법

### Arduino Uno와 ETH-01D 연결

![133](https://user-images.githubusercontent.com/94042419/223014118-30db5f7f-008c-4b83-867d-00936066e8f0.PNG)

### Arduino MKR와 ETH-01D 연결

![134](https://user-images.githubusercontent.com/94042419/223014031-7a1b3d41-dde4-45d2-88d6-ed1ff37667cd.PNG)

### ESP32-S2와 ETH-01D 연결


![135](https://user-images.githubusercontent.com/94042419/223014054-76b43316-ba7e-42f2-a0dc-15344bd61b65.PNG)

※ 핀 연결에 따른 소스코드 변경사항

Void setup() 부분에서 Wire.begin() -> Wire.begin(7,8,5000)으로 변경

### ESP8266-12E와 ETH-01D 연결

![136](https://user-images.githubusercontent.com/94042419/223014075-0ccd48a6-a766-486e-b89f-e4f8f43ecca6.PNG)


※ 핀 연결에 따른 소스코드 변경사항

Void setup() 부분에서 Wire.begin() -> Wire.begin(4,5,5000)으로 변경,

\#define Sensor\_power\_port 6 -> #define Sensor\_power\_port 16으로 변경
