---
description: NevadaNano 제품의 출고 제품 버전별 변경사항을 공유하고있습니다.
---

# 3.0/4.0/5.0 Version 변경사항

## 요약

**(3.0 version -> 4.0, 5.0 version)**

1\. UART 통신 - 센서 상태 Command 버전 증가할수록 기능 추가

2\. 동작 Sequence 변경에 따른 센서 초기화 구간 및 시간 변경

3\. Analog - output 5.0에서 2.4V로 변경, 센서 상태 버전 증가할수록 기능 추가

4\. 소모전력 5.0에서 1.7mW 감소함(+3V 기준)

* [MPS Flammable Gas Sensor User Manual](https://nevadanano.com/wp-content/uploads/2023/05/SM-UM-0002-24-MPS-Flammable-Gas-Sensor-User-Manual.pdf)
* [MPS Flammable Gas Sensor 4.0 User Manual](https://nevadanano.com/wp-content/uploads/2023/05/SM-UM-0007-05-MPS-Flammable-Gas-Sensor-4.0-User-Manual.pdf)
* [MPS Flammable Gas Sensor 5.0 User Manual](https://nevadanano.com/wp-content/uploads/2023/05/SM-UM-0010-03-MPS-Flammable-Gas-Sensor-5.0-User-Manual.pdf)

## Status Command (Hex)

* Status Command는 센서에게 특정 Command(ex. 가스 값 요청 Command)를 요청하였을 때 센서에서 현재 센서의 상태를 나타내어 주는 Command임
*   변경사항:

    > 기존 -> 4.0 Status Command 0x27, 0x33, 0x34 추가, 0x35 삭제 -> 5.0 Status Command 0x35\~0x38 추가

| 기존   | 기존              | 4.0  | 4.0                                  | 5.0  | 5.0                                  |
| ---- | --------------- | ---- | ------------------------------------ | ---- | ------------------------------------ |
| -    | -               | 0x27 | 센서 초기화 (동작 Sequence 변경 되면서 추가됨)      | 0x27 | 센서 초기화 (동작 Sequence 변경 되면서 추가됨)      |
| 0x30 | 센서 출력〈-15%LEL   | 0x30 | 센서 출력〈-150/6LEL                      | 0x30 | 센서 출력< -15%LEL                       |
| 0x31 | 센서 결로 상태        | 0x31 | 센서 결로 상태                             | 0x31 | 센서 결로 상태                             |
| 0x32 | 가스감지소자 부조       | 0x32 | 가스감지소자 error                         | 0x32 | 가스감지소자 error                         |
| -    | -               | 0x33 | 가스 감지 (동작 Sequence 변경 되면서 추가됨)       | 0x33 | 가스 감지 (동작 Sequence 변경 되면서 추가됨)       |
| -    | -               | 0x34 | 느린 축적 가스 감지 (동작 Sequence 변경 되면서 추가됨) | 0x34 | 느린 축적 가스 감지 (동작 Sequence 변경 되면서 추가됨) |
| 0x35 | 사람의 호흡이나 습도가 급증 | -    | -                                    | 0x35 | 사람의 호흡이나 습도가 급증                      |
| -    | -               | -    | -                                    | 0x36 | Watchdog 리A;人21                      |
| -    | -               | -    | -                                    | 0x37 | Watchdog error                       |
| -    | -               | -    | -                                    | 0x38 | ADC or DAC error                     |

## 동작 시간

* Version 변경 후 센서 초기화 구간이 변경되었고, 초기화에 걸리는 시간이 변경됨

| 구분                 | 기존               | 4.0                             | 5.0                         |
| ------------------ | ---------------- | ------------------------------- | --------------------------- |
| 센서 초기화 구간          | 기존 전원 킨 직후       | 측정 모드                           | 측정 모드                       |
| 초기화 걸리는 시간(max 기준) | 3초boot)+20초= 23초 | 3초(boot)+104초(warm up)+14초=121초 | 3초(boot)+31초+32초 +12초 = 78초 |

* 4.0 warm up(104초) 기간 동안 -100 %LEL 및 ID = 253을 보고하며 가스를 감지함

## 아날로그 출력

* Analog out 3.0과 4.0은 2.9V로 동일하며 5.0은 2.4V로 감소함

<figure><img src="../../.gitbook/assets/p01 (2).webp" alt="아날로그 출력 비교"><figcaption><p>아날로그 출력 비교</p></figcaption></figure>

* 3.0에서 4.0, 5.0로 upgrade 되면서 센서 상태 확인 추가된 기능

| 4.0                        | 5.0                        |
| -------------------------- | -------------------------- |
| Analog out 실행 가능(제조사에서 실행) | Analog out 실행 가능(제조사에서 실행) |
| 초기 전원 전원 on 후 가스 감지 기능     | 초기 전원 전원 on 후 가스 감지 기능     |
| -                          | Watchdog 에러 감지             |
| -                          | ADC, DAC 변위 에러 감지          |

## 소모 전력

* 3.0, 4.0에서 5.0으로 변화하면서 소모전력이 1.7mW 감소함(+3V 기준)
