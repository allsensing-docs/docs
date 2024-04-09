---
description: >-
  AGSM is a sensor module that can be used with Arduino.
---

# AGSM Arduino Application

## Wiring Method

{% tabs %}
{% tab title="Arduino Uno #1" %}
<figure><img src="p2_image/arduino_connection1.webp" alt="AGSM Connection1" width="563"><figcaption><p>AGSM Arduino</p></figcaption></figure>
{% endtab %}

{% tab title="Arduino Uno #2" %}
<figure><img src="p2_image/arduino_connection2.webp" alt="AGSM Connection2" width="563"><figcaption><p>AGSM Arduino</p></figcaption></figure>
{% endtab %}
{% endtabs %}

## Arduino UNO Example Code

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

## Arduino Serial monitor

<figure><img src="p2_image/AGSMSerialCommunication.webp" alt="agsm Serial monitor" width="563"><figcaption><p>AGSM Serial Monitor</p></figcaption></figure>
