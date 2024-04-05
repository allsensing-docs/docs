# DUAL Toxic

## 특징

\- 한 개의 센서에 두가지의 가스(일산화탄소(CO), 황화수소(H2S))를 측정

\- 일반적인 전극 4개(작업(Working)전극 1, 작업(Working)전극2, 기준(Reference)전극, 상대(Counter or Auxiliary) 전극 로 이루어져 있으며, 전극 사이에 전위차를 생성하여 전류를 측정

\- 작업(Working)전극 1, 작업(Working)전극2로 각각 일산화탄소(CO), 황화수소(H2S) 전류 출력

|        모델       |
| :-------------: |
| Dcel DT, GS+4DT |

<figure><img src="../../../.gitbook/assets/DDS GS+4DT.jpeg" alt="" width="250"><figcaption><p>&#x3C;GS+4DT></p></figcaption></figure>

## Reference 회로도

<figure><img src="../../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

* H2S CHANNEL SIGNAL OUT = Vref + ((Sensitivity \* gas concentration) \* R6)
* CO CHANNEL SIGNAL OUT = Vref + ((Sensitivity \* gas concentration) \* R8)
