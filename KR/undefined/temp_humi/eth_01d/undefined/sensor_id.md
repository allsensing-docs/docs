# Sensor ID 읽기

**Step 1. ETH-01D I2C command 전송**

* Device에서 command(i2c Address(0x44),0xa0,0x00,0x00)를 ETH-01D로 전송

![](https://user-images.githubusercontent.com/94042419/223005738-15bb6f18-0faa-4503-b485-f72fdd97a707.png)

**Step 2. 상위 Sensor ID 요청 Command**

* Device에서 Command((i2c Address+Write bit),0x1E(ID 상위 바이트), 0x00, 0x00)를 ETH-01D로 전송 후 120 μs 기다림

![](https://user-images.githubusercontent.com/94042419/223005827-d6309df7-4547-4f63-8718-fa9c5cebe265.png)

**Step 2.1. 상위 Sensor ID 응답**

* Sensor ID 상위 바이트(16bit)를 읽음

![](https://user-images.githubusercontent.com/94042419/223005843-5f489537-67de-4213-aa36-b587cc8599e7.png)

**Step 3. 하위 Sensor ID 요청 Command**

* Device에서 Command ((i2c Address+Write bit),0x1F(ID 하위 바이트), 0x00, 0x00)를 ETH-01D로 전송 후 120 μs 기다림

![](https://user-images.githubusercontent.com/94042419/223005858-ed867bf8-10f2-44cd-b511-4703ad68cbd7.png)

**Step 3.1 하위 Sensor ID 응답**

* Device에서 Command ((i2c Address+Write bit),0x1F(ID 하위 바이트), 0x00, 0x00)를 ETH-01D로 전송 후 120 μs 기다림

![](https://user-images.githubusercontent.com/94042419/223005871-695f77e1-a010-4c93-9f25-ff26207f96a9.PNG)

## 소스 코드

{% tabs %}
{% tab title="Sensor id 읽기 code" %}
```cpp
#include <Wire.h>
#define slave_address 0x44
#define Sensor_power_port 6 // Arduino uno, Arduino mkr 1010, esp32
//#define Sensor_power_port 16 //esp8266
#define Power_enable digitalWrite(Sensor_power_port, HIGH)
#define Power_disable digitalWrite(Sensor_power_port, LOW)
void setup()
{
Wire.begin(); // Arduino uno, Arduino mkr 1010
// Wire.begin(7,8,5000); //esp32
// Wire.begin(4,5,5000); //esp8266
Serial.begin(9600);
pinMode(Sensor_power_port, OUTPUT);
}
void loop()
{
int Status;
int RegisterValueHigh;
int RegisterValueLow;
//===Module Power Reset===
Power_disable;
delay(1);
Power_enable;
delay(2); //10msec 이내에 신호 전송되어야함
// 레지스터 주소 쓰기===
//프로그래밍 모드로 들어가기 위한 명령, 명령어 처리 시까지 120usec 시간이 소요됨.
Wire.beginTransmission(slave_address);
Wire.write(0xA0);
Wire.write(0x00);
Wire.write(0x00);
Wire.endTransmission();
delayMicroseconds(120);
//Sensor 상위 id 요청
Wire.beginTransmission(slave_address);
Wire.write(0x1E);
Wire.write(0x00);
Wire.write(0x00);
Wire.endTransmission();
delay(1);
//Sensor 상위 id 응답
Wire.requestFrom(slave_address, 3);
if (Wire.available()) {
Status = Wire.read();
RegisterValueHigh = Wire.read();
RegisterValueLow = Wire.read();
Serial.print(" Sensor id_high: ");
Serial.print(Status, HEX); // status success = 0x81
Serial.print(" ");
Serial.print(RegisterValueHigh, HEX);
Serial.print(" ");
Serial.println(RegisterValueLow, HEX);
}
//Sensor 하위 id 요청
Wire.beginTransmission(slave_address);
Wire.write(0x1F);
Wire.write(0x00);
Wire.write(0x00);
Wire.endTransmission();
delay(1);
//Sensor 하위 id 응답
Wire.requestFrom(slave_address, 3);
if (Wire.available()) {
Status = Wire.read();
RegisterValueHigh = Wire.read();
RegisterValueLow = Wire.read();
Serial.print(" Sensor id_low: ");
Serial.print(Status, HEX); // status success = 0x81
Serial.print(" ");
Serial.print(RegisterValueHigh, HEX);
Serial.print(" ");
Serial.println(RegisterValueLow, HEX);
}
// 프로그래밍 모드에서 일반 모드로 전환
Wire.beginTransmission(slave_address);
Wire.write(0x80);
Wire.write(0x00);
Wire.write(0x00);
Wire.endTransmission();
delay(1000);
}
```
{% endtab %}
{% endtabs %}

* Sensor id 읽기 시리얼 모니터

![](https://user-images.githubusercontent.com/94042419/223005908-bd0e7866-0463-4315-b584-e59015b3d9d4.png)
