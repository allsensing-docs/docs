# 통신 프로토콜

* UART 설정

| PARAMETER         | TYP      |
| ----------------- | -------- |
| Baud Rate (Fixed) | 9600 bps |
| Data Bits         | 8        |
| Parity            | None     |
| Stop Bits         | 1        |
| Flow Control      | None     |



* Uart 전체 Command

<figure><img src="../../../../.gitbook/assets/all_uart_command.PNG" alt=""><figcaption></figcaption></figure>

## 모듈 정보 읽기

{% content-ref url="undefined-1/undefined.md" %}
[undefined.md](undefined-1/undefined.md)
{% endcontent-ref %}

## 모드 설정 및 가스 센서 값 읽기

{% content-ref url="undefined-1/undefined-1.md" %}
[undefined-1.md](undefined-1/undefined-1.md)
{% endcontent-ref %}



## &#x20;LED 제어

&#x20;

| 기 능     | Command (HEX)              | Response |
| ------- | -------------------------- | -------- |
| LED off | FF 01 88 00 00 00 00 00 77 | 4F FB    |
| LED on  | FF 01 89 00 00 00 00 00 76 | 4F FB    |

체크섬(Checksum) 설명

&#x20;

<figure><img src="../../../../.gitbook/assets/checksum_one.PNG" alt=""><figcaption></figcaption></figure>

Data 1\~7 byte 값을 전부 더 하고 1의 보수를 취하고 1을 더함

Ex.1)

| <p>Data 1~7 byte 전부 더함 = 0x01 +0x86 = 0x87 = 1000 0111</p><p>= 0111 1000 = 0x78</p><p>= 0x78 +1</p><p>= 0x79</p> |
| ---------------------------------------------------------------------------------------------------------------- |

&#x20;

<figure><img src="../../../../.gitbook/assets/checksum_two.PNG" alt=""><figcaption></figcaption></figure>

&#x20;

Ex.2)

| <p>Data 1~7 byte 전부 더함 = 0x86 +0x2A+0x20 = 0xD0 = 1101 0000</p><p>= 0010 1111 = 0x2f</p><p>= 0x2f +1</p><p>= 0x30</p> |
| --------------------------------------------------------------------------------------------------------------------- |







