---
description: >-
  AGSM은 아두이노와 함께 사용할 수 있는 센서 모듈입니다.  아두이노 UNO 보드와 함께 사용하여 센서값을 모니터링에 활용할 수
  있습니다. 센서 연결 방법, 예제 코드를 통해 다양한 환경 정보를 측정하고 분석할 수 있습니다.
---

# AGSM 아두이노 활용

<!-- 메인 이미지 
<figure><img src="p2_image/card_asgm_arduino.webp" alt="agsm arduino" width="563"><figcaption><p>AGSM Arduino</p></figcaption></figure>
-->

## 와이어 결선 방법

{% tabs %}
{% tab title="Arduino Uno #1" %}
<figure><img src="p2_image/arduino_connection1.webp" alt="AGSM Connection1" width="563"><figcaption><p>AGSM Arduino</p></figcaption></figure>
{% endtab %}

{% tab title="Arduino Uno #2" %}
<figure><img src="p2_image/arduino_connection2.webp" alt="AGSM Connection2" width="563"><figcaption><p>AGSM Arduino</p></figcaption></figure>
{% endtab %}
{% endtabs %}

## 아두이노 UNO 예제코드

{% tabs %}
{% tab title="Arduino Uno" %}
```c
#include <SoftwareSerial.h>
 
#define ContinueMode 0
#define PollingMode 1
 
const int rxPin = 2;
const int txPin = 3;
SoftwareSerial Serial1(rxPin, txPin);
 
void setup()
{
  Serial.begin(9600);
  Serial1.begin(9600);//AGSM sensor module connection
  delay(1000);
 
  #if ContinueMode
  Serial.println("Continuous Mode");
  #else if PollingMode
  Serial.println("Polling Mode");
  #endif
  Serial.println("Serial, Conc.(PPB), Temp.(C), Rh(%), Adc.(Counts), Temp.(Counts), Rh(%Counts)");
  #if ContinueMode
  Serial1.write('c');
  Serial1.write('\r');
  #endif
}
 
void loop()
{
  #if PollingMode
    Serial1.write('\r');
    delay(1000);
  #else
    delay(100);
  #endif
   while (Serial1.available()) // read from AGSM port, send to Serial port to interupt continuous output send 'c''/r' without line ending, may have to send more than once.
  {
   int inByte = Serial1.read();
   Serial.write(inByte);   
  }
}
```
{% endtab %}
{% endtabs %}

## 아두이노 시리얼 모니터 출력

<figure><img src="p2_image/AGSMSerialCommunication.webp" alt="agsm Serial monitor" width="563"><figcaption><p>AGSM Serial Monitor</p></figcaption></figure>
