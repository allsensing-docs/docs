# 디바이스 연결 방법

## Connection DIAGRAM (UART)

<figure><img src="../../../.gitbook/assets/connetion_uart_diagram.PNG" alt=""><figcaption></figcaption></figure>



{% tabs %}
{% tab title="Arduino Uno" %}
<figure><img src="../../../.gitbook/assets/LOX_O2_with_uno.PNG" alt=""><figcaption></figcaption></figure>

| 항목  | Arduino Uno | Lox-O2 |
| --- | ----------- | ------ |
| VCC | 5V          | VCC    |
| GND | GND         | GND    |
| TX  | 12          | RX     |
| RX  | 13          | TX     |
{% endtab %}

{% tab title="Arduino MKR" %}
<figure><img src="../../../.gitbook/assets/LOX_O2_with_mkr.PNG" alt=""><figcaption></figcaption></figure>

| 항목  | Arduino MKR | Lox-O2 |
| --- | ----------- | ------ |
| VCC | 5V          | VCC    |
| GND | GND         | GND    |
| TX  | 14          | RX     |
| RX  | 13          | TX     |
{% endtab %}

{% tab title="ESP32" %}
<figure><img src="../../../.gitbook/assets/LOX_O2_with_esp32.PNG" alt=""><figcaption></figcaption></figure>

| 항목  | ESP32 | Lox-O2 |
| --- | ----- | ------ |
| VCC | 5V    | VCC    |
| GND | GND   | GND    |
| TX  | 17    | RX     |
| RX  | 18    | TX     |
{% endtab %}

{% tab title="ESP8266" %}
<figure><img src="../../../.gitbook/assets/LOX_O2_with_esp8266.PNG" alt=""><figcaption></figcaption></figure>

| 항목  | ESP8266 | Lox-O2 |
| --- | ------- | ------ |
| VCC | 5V      | VCC    |
| GND | GND     | GND    |
| TX  | 13      | RX     |
| RX  | 15      | TX     |
{% endtab %}
{% endtabs %}



