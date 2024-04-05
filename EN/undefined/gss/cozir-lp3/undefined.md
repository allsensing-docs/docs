# 디바이스 연결 방법

## Connection DIAGRAM (UART)

<figure><img src="../../../.gitbook/assets/connetion_uart_diagram.PNG" alt=""><figcaption></figcaption></figure>

## Connection DIAGRAM (I2C)

<figure><img src="../../../.gitbook/assets/CozIR-Blink_connetion_diagram_i2c.PNG" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="Arduino Uno Uart" %}
<figure><img src="../../../.gitbook/assets/Cozir_series_uart_connection_with_arduino_uno.PNG" alt=""><figcaption></figcaption></figure>

|  항목 | Arduino Uno | Cozir-LP3 |
| :-: | :---------: | :-------: |
| VCC |  5V or 3.3V |    VCC    |
| GND |     GND     |    GND    |
|  TX |      13     |     RX    |
|  RX |      12     |     TX    |
{% endtab %}

{% tab title="Arduino Uno  I2C" %}
<figure><img src="../../../.gitbook/assets/Cozir_series_i2c_connection_with_arduino.PNG" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="140" align="center">항목</th><th align="center">Arduino Uno</th><th align="center">Cozir-LP3</th></tr></thead><tbody><tr><td align="center">VCC</td><td align="center">5V or 3.3V</td><td align="center">VCC</td></tr><tr><td align="center">GND</td><td align="center">GND</td><td align="center">GND</td></tr><tr><td align="center">TX</td><td align="center">A5</td><td align="center">SCL</td></tr><tr><td align="center">RX</td><td align="center">A4</td><td align="center">SDA</td></tr></tbody></table>
{% endtab %}

{% tab title="Arduino MKR Uart" %}
<figure><img src="../../../.gitbook/assets/cozir_lp2_arduino_uno_2.PNG" alt=""><figcaption></figcaption></figure>

|  항목 | Arduino MKR | Cozir-LP3 |
| :-: | :---------: | :-------: |
| VCC |  5V or 3.3V |    VCC    |
| GND |     GND     |    GND    |
|  TX |      13     |     RX    |
|  RX |      12     |     TX    |
{% endtab %}

{% tab title="Arduino MKR I2C" %}
<figure><img src="../../../.gitbook/assets/CozIR-LP2_with_Arduino_MKR_i2c.png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="140" align="center">항목</th><th align="center">Arduino MKR</th><th align="center">Cozir-LP3</th></tr></thead><tbody><tr><td align="center">VCC</td><td align="center">5V or 3.3V</td><td align="center">VCC</td></tr><tr><td align="center">GND</td><td align="center">GND</td><td align="center">GND</td></tr><tr><td align="center">TX</td><td align="center">D11</td><td align="center">SCL</td></tr><tr><td align="center">RX</td><td align="center">D12</td><td align="center">SDA</td></tr></tbody></table>
{% endtab %}

{% tab title="ESP32 Uart" %}
<figure><img src="../../../.gitbook/assets/CozIR-LP2_with_ESP32.PNG" alt=""><figcaption></figcaption></figure>

|  항목 |    ESP32   | Cozir-LP3 |
| :-: | :--------: | :-------: |
| VCC | 5V or 3.3V |    VCC    |
| GND |     GND    |    GND    |
|  TX |      5     |     RX    |
|  RX |      6     |     TX    |
{% endtab %}

{% tab title="Esp32 I2C" %}
<figure><img src="../../../.gitbook/assets/cozirlp2_ESP32_I2C.png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="140" align="center">항목</th><th align="center">ESP32</th><th align="center">Cozir-LP3</th></tr></thead><tbody><tr><td align="center">VCC</td><td align="center">5V or 3.3V</td><td align="center">VCC</td></tr><tr><td align="center">GND</td><td align="center">GND</td><td align="center">GND</td></tr><tr><td align="center">TX</td><td align="center">13</td><td align="center">SCL</td></tr><tr><td align="center">RX</td><td align="center">12</td><td align="center">SDA</td></tr></tbody></table>
{% endtab %}

{% tab title="ESP8266 Uart" %}
<figure><img src="../../../.gitbook/assets/cozir_lp2_with_ESP8266.PNG" alt=""><figcaption></figcaption></figure>

|  항목 | ESP8266 | Cozir-LP3 |
| :-: | :-----: | :-------: |
| VCC |   3.3V  |    VCC    |
| GND |   GND   |    GND    |
|  TX |    15   |     RX    |
|  RX |    13   |     TX    |
{% endtab %}

{% tab title="ESP8266 I2C" %}
<figure><img src="../../../.gitbook/assets/CozIR-LP2_with_ESP8266_I2C.png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="140" align="center">항목</th><th align="center">ESP8266</th><th align="center">Cozir-LP3</th></tr></thead><tbody><tr><td align="center">VCC</td><td align="center">5V or 3.3V</td><td align="center">VCC</td></tr><tr><td align="center">GND</td><td align="center">GND</td><td align="center">GND</td></tr><tr><td align="center">TX</td><td align="center">D5</td><td align="center">SCL</td></tr><tr><td align="center">RX</td><td align="center">D6</td><td align="center">SDA</td></tr></tbody></table>
{% endtab %}
{% endtabs %}

<figure><img src="../../../.gitbook/assets/cozir_lp3_i2c_실제사진.jpg" alt=""><figcaption></figcaption></figure>
