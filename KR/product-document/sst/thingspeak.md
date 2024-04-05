# Thingspeak 활용 방법

{% embed url="https://thingspeak.com/channels/1614699" %}



Step1. 아두이노 IDE에 Thingspeak 라이브러리 추가

![148](https://user-images.githubusercontent.com/94042419/223014285-130709bd-c600-4ffe-8ece-be0cb6fd131e.PNG)

Step2. Wi-Fi ssid, pass 확인 및 변경

* code Thingspeak ssid, password 부분 자신이 사용할 Wi-Fi ssid, pass로 변경

Step3. Thingpeak channelnumber 및 api key 확인

* Thingspeak -> channel -> my channel -> channel setting -> channel id 확인 후 code 변경
* Thingspeak -> channel -> my channel -> Api keys -> Write Api key -> key 확인 후 code 변경

## 소스 코드

{% tabs %}
{% tab title="Thingspeak" %}
```cpp
#include <Arduino.h>
#include "ThingSpeak.h"
#include <Wire.h>
#include <WiFi.h>
const char* Poll_mode = "M 01\r\n";
const char* O2_Read = "%\r\n";
const char* ssid = "your network SSID";   // your network SSID (name) 
const char* password = "your network password";   // your network password
WiFiClient  client;
unsigned long myChannelNumber = your channel number;
const char * myWriteAPIKey = "your channel api key";
// Timer variables
String str;
unsigned long lastTime = 0;
unsigned long timerDelay = 10000;
void setup()
{
Serial.begin(9600);
  WiFi.mode(WIFI_STA);   
  ThingSpeak.begin(client);  // Initialize ThingSpeak
}
void loop()
{
float o2_value_to;
  Serial1.print(O2_Read);
  delay(1000);
   if(Serial1.available()>0) 
   { 
    str = "";
    str = Serial1.readStringUntil('\n'); 
    Serial.println(str);
    int o2_length  = str.length();
    String value_o2 = str.substring(o2_length-6, o2_length);
    o2_value_to = value_o2 .tofloat();
   }

    if ((millis() - lastTime) > timerDelay) 
    {
        // Connect or reconnect to WiFi
        if(WiFi.status() != WL_CONNECTED)
        {
        Serial.print("Attempting to connect");
        while(WiFi.status() != WL_CONNECTED){
            WiFi.begin(ssid, password); 
            delay(2000);     
        } 
        Serial.println("\nConnected.");
        }
        // pieces of information in a channel.  Here, we write to field 1.
        ThingSpeak.setField(1, o2_value_to);
        int x = ThingSpeak.writeFields(myChannelNumber, myWriteAPIKey);
        if(x == 200){
        Serial.println("Channel update successful.");
        }
        else{
        Serial.println("Problem updating channel. HTTP error code " + String(x));
        }
        lastTime = millis();
   }

```
{% endtab %}
{% endtabs %}
