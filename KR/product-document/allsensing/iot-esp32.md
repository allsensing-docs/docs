---
description: >-
  AGSM은 ESP32 모듈과 함께 사용할 수 있는 센서 모듈입니다.  ESP32 보드와 함께 사용하여 IoT플랫폼과 연동하여 센서 값을
  모니터링에 활용할 수 있습니다.  센서 연결 방법, 예제 코드를 통해 다양한 환경 정보를 측정하고 분석할 수 있습니다.
---

# AGSM IoT 활용(ESP32)

<!-- 메인 이미지 
<figure><img src="p3_image/card_asgm_esp32.webp" alt="agsm esp32" width="563"><figcaption><p>AGSM ESP32</p></figcaption></figure>
-->

## 소개

이 프로젝트에서는 ESP32를 사용하여 센서 판독값을 ThingSpeak로 보내는 방법에 대해서 이야기 합니다.\
이 프로젝트에서는 AGSM 센서를 사용하지만 다른 센서를 사용하도록 예제를 쉽게 수정할 수 있습니다.

ThingSpeak를 사용하면 센서 판독값을 웹 사이트에 게시하고 타임스탬프가 지정된 차트에 표시할 수 있습니다.\
또한 MATLAB 시각화를 사용하여 그래프를 시각화하고 전 세계 어디에서나 판독값에 액세스할 수 있습니다.

센서 판독값을 ThingSpeak로 보내는 방법에는 여러 가지가 있습니다. 이 프로젝트는 [thingspeak-arduino](https://github.com/mathworks/thingspeak-arduino) 라이브러리를 사용합니다. GitHub 페이지에서 라이브러리 예제를 볼 수 있습니다.

## 필요한 것들

1. ESP32-DevKitC
2. AGSM\_CO

<figure><img src="p3_image/agsm_esp32connection.webp" alt="AGSM ESP32r" width="563"><figcaption><p>AGSM ESP32 Connection</p></figcaption></figure>

## 예제 코드

```c

#include <Arduino.h>
#include <WiFi.h>
#include "ThingSpeak.h"
// WIFI Settings
#define WIFI_SSID                "your wifi ssid"       
#define WIFI_PASSWORD            "your wifi pass"

//---UART2--------
#define RXD2 16
#define TXD2 17
int Uart2ReceiveLength = 0;


WiFiClient client;

// Thingspeak Timer variables
unsigned long lastTime = 0;
unsigned long timerDelay = 30000;

int AGSM_gas_value[8]={0}; 

// Thingspeak interface
const char* myWriteAPIKey = "your write apikey"; 
unsigned long myChannelNumber = "your channelnumber";  

#define ContinueMode 1
#define PollingMode 0
const int BUFFER_SIZE = 100;
char buf[BUFFER_SIZE];
int inByte = 0;
char tempChars[100];    
int ppb=0;
float ppm=0.000;
float temp=0;
float rh=0;
int Serial_number=0;
int ADC_value; // AGSM Module adc value

void setup()
{
  Serial.begin(115200);  
  Serial2.begin(9600, SERIAL_8N1, RXD2, TXD2); // Sensor connection port

  #if ContinueMode
  Serial.println("Continuous Mode");
  #else if PollingMode
  Serial.println("Polling Mode");
  #endif
  Serial.println("Serial, Conc.(PPB), Temp.(C), Rh(%), Adc.(Counts), Temp.(Counts), Rh(%Counts)");
  #if ContinueMode
  Serial2.write('c');
  Serial2.write('\r');
  #endif
  ThingSpeak.begin(client);  // Initialize ThingSpeak
}

void parseData() 
{      // split the data into its parts

    char * strtokIndx; // this is used by strtok() as an index
    //SN [XXXXXXXXXXXX], PPB [0 : 999999], TEMP [-99 : 99], RH [0 : 99], RawSensor[ADCCount], TempDigital, RHDigital, Day [0 : 99], Hour [0 : 23], Minute [0 : 59], Second [0 : 59]

    //length is variable LEN= 50 DATA= 071421030446, 875, 23, 19, 2111737, 23956, 19605
        strtokIndx = strtok(buf,",");      // get the first part - the string
        Serial_number = atoi(strtokIndx); 

        strtokIndx = strtok(NULL,",");     
        ppb = atoi(strtokIndx); 
        
        strtokIndx = strtok(NULL, ","); 
        temp = atoi(strtokIndx);  

        strtokIndx = strtok(NULL, ","); 
        rh = atoi(strtokIndx);  

        strtokIndx = strtok(NULL, ",");
        ADC_value = atoi(strtokIndx); 
	
        AGSM_gas_value[0]=(float)(ppb);
	
   	// AGSM Module data
        Serial.print("   ppb= ");
        Serial.print(ppb);
        Serial.print("  Temperature= ");
        Serial.print(temp);
        Serial.print("  Humidity= ");
        Serial.print(rh);
        Serial.print("  ADC= ");
        Serial.print(ADC_value);
        Serial.println(" ");

    for(int i=0; i<inByte;i++)
		buf[i]=0;
}
void loop()
{
   while (Serial2.available()) // read from AGSM port, send to Serial port to interupt continuous output send 'c''/r' without line ending, may have to send more than once.
  {
        inByte = Serial2.readBytesUntil('\n', buf, BUFFER_SIZE);
        parseData(); 
  }
  if ((millis() - lastTime) > timerDelay) 
  {
    // Connect or reconnect to WiFi
    if(WiFi.status() != WL_CONNECTED){
      Serial.print("Attempting to connect");
      while(WiFi.status() != WL_CONNECTED){
        WiFi.begin(WIFI_SSID, WIFI_PASSWORD); 
        delay(5000);     
      } 
      Serial.println("\nConnected.");
    }
    if((AGSM_gas_value[0]>=0) && (AGSM_gas_value[0] < 50000))
    { 
       // set the fields with the values
      ThingSpeak.setField(1, AGSM_gas_value[0]);
      int x = ThingSpeak.writeFields(myChannelNumber, myWriteAPIKey);
      if(x == 200){
      Serial.println("Channel update successful.");
      }
      else{
      Serial.println("Problem updating channel. HTTP error code " + String(x));
      }
      lastTime = millis();
      }
    }
}
```
