# 배경지식

**전기화학식 센서:**

* 측정된 가스와 화학 반응을 일으키고 기체 농도에 비례하는 전류를 발생시키게 되고 그 전류의 세기를 통해서 가스농도를 측정함
* 출력 선형성, 저전력 소모, 우수한 분해능, 뛰어난 반복성 및 정확도
* 가스와의 화학반응에 따른 전류 신호를 출력하며 사용할수록 소모되기 때문에 수명이 있음

**바이어스:**

전압이나 전류의 동작점을 미리 결정하는 것(외부에서 직류 전압/전류 인가)

* 전기화학식 가스 센서에는 바이어스 회로가 필요함, 일반적으로 바이어스 전압은 0mV이지만 일부 가스 센서에서 양수(positive) or 음수(negative) 바이어스가 요구됨
* 바이어스 회로의 목적은 작업전극 전위를 기준전극에 대해 일정하게 유지시키는 것, 이 역할은 상대전극 전압을 조정하여 수행됨
* 바이어스 식: (작업(Working= sense)전극- 기준(Reference))
* 바이어스 센서: 전위차 회로(WE, RE)가 필요한3개의 전극이 있는 센서

※ 잘못된 바이어스 전압 공급 시 센서가 손상될 수 있음

<figure><img src="../../.gitbook/assets/image (7).png" alt="출저-analog device" width="530"><figcaption><p>&#x3C;전기화학식 3전극 가스 센서 회로 다이어그램> 출처 - analog devices</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (54).png" alt="" width="563"><figcaption><p>&#x3C;전기화학식 3전극 가스 센서 0mV 바이어스 회로> 출처 - SGX sensor</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (15).png" alt="" width="563"><figcaption><p>&#x3C;전기화학식 3전극 가스 센서 +300mV 바이어스 회로 > 출처 - SGX sensor</p></figcaption></figure>

* Vout 극성 : 대부분의 가스 전자는 작업 전극으로 흐르지만(+V) 셀에서 환원되는 가스(ex) ClO2, CL2, NO2, O2)에 경우 전자의 방향이 달라짐(-V)

전기화학식 센서 주의사항

* 센서에 직접 Soldering 진행 시 내부의 패턴이 고온으로 끊어질 수 있으므로 전용 Socket을 사용 권장
* 센서에 따른 감도가 차이가 있기 때문에 회로를 구성한 이후 개별 가스 교정이 필요(교정 Cap 필요)
* 가스 교정설비가 없을 경우, 모듈 type의 센서를 사용하거나 가스 교정설비를 구입할 것을 권장함

<figure><img src="../../.gitbook/assets/Socket" alt=""><figcaption><p>&#x3C;전용 Socket></p></figcaption></figure>
