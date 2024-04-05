# 통신 프로토콜

## UART 설정

|       PARAMETER       |  TYP |  UNIT  |
| :-------------------: | :--: | :----: |
|       Buad Rate       | 9600 | Bits/s |
|       Data Bits       |   8  |        |
|         Parity        | None |        |
|       Stop Bits       |   1  |        |
| Hardware Flow Control | None |        |

{% content-ref url="co2.md" %}
[co2.md](co2.md)
{% endcontent-ref %}

{% content-ref url="uart-i2c-co2.md" %}
[uart-i2c-co2.md](uart-i2c-co2.md)
{% endcontent-ref %}

{% content-ref url="digital-filter.md" %}
[digital-filter.md](digital-filter.md)
{% endcontent-ref %}

<table><thead><tr><th width="156">Command</th><th>Description</th><th>Response</th></tr></thead><tbody><tr><td>K 0</td><td>Command를 기다리는 상태, 측정 X</td><td>K 00000</td></tr><tr><td>K 1</td><td>연속적으로 값을 측정</td><td>K 00001</td></tr><tr><td>K 2</td><td>센서 값 요청시에만 응답</td><td>K 00002</td></tr><tr><td>Z</td><td>가장 최근에 측정한 CO2 필터 된 값</td><td>Z 00521</td></tr><tr><td>z</td><td>가장 최근에 측정한 CO2 필터 되지 않은 값</td><td>z 00521</td></tr><tr><td>A ###</td><td>CO2 필터 값 설정</td><td>A 00016</td></tr><tr><td>a</td><td>CO2 필터 값 확인</td><td>a 00016</td></tr><tr><td>U</td><td>질소를 사용하여 제로 교정</td><td>U 33000</td></tr><tr><td>u</td><td>초기 설정 값으로 제로 교정</td><td>u</td></tr><tr><td>G</td><td>Fresh Air를 사용하여 제로 교정</td><td>G 33000</td></tr><tr><td>X #####</td><td>현재 값으로 스팬 교정</td><td>X 11000</td></tr><tr><td><p>P 10###</p><p>P 11###</p></td><td>Fresh Air에서 사용할 대기 중 농도를 설정(default 400ppm)</td><td>Fresh Air에서 사용할 대기 중 농도를 설정(default 400ppm)</td></tr><tr><td>S ###</td><td>고도 설정</td><td>S 08192</td></tr><tr><td>s</td><td>고도 설정 값 확인</td><td>s 08192</td></tr><tr><td>M ###</td><td>측정 데이터 문자열로 전송</td><td>M 6</td></tr></tbody></table>
