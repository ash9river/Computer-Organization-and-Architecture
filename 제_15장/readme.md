# 축소 명령어 세트 컴퓨터 : RISC

> 들어가기에 앞서, 컴퓨터 조직과 아키텍처의 저자는 CISC보다 RISC가 좀 더 좋다는 편향적인 생각을 가지고 있음을 밝힌다.

## RISC vs CISC

- *Computer*
  - `CISC(Complex : *intel PC*)` : 복잡한 data access(High Level Language에 최적화)
  - `RISC(Reduced : *ARM*)` : Embedded, Mobile 등 간단한 기기에 맞춰, 단순한 명령어 세트, 단순한 data access

### 몇 가지 CISC, RISC 및 슈퍼스칼라 프로세서의 특징들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/0d170bf9-4824-4524-96ee-5b3281de3e68">

<br/>
<br/>

## 명령어 실행 특성들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/dc138aa2-ad08-4e89-babd-ea214f774425

<br/>

### HLL 연산들의 상대적 동적 빈도

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/b42c3bee-db67-451c-b081-28ab50776d3c">

<br/>

### 오퍼랜드들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/f9b24018-659d-4347-93ce-41c86b2e7116">

<br/>

### 프로시저 변수들과 지역 스칼라 변수들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/b41a4b04-00d9-45b4-8083-697f0d1baacd">

<br/>

## 제안들(RISC)

- HLL 프로그램에서 가장 많은 시간을 소비하는 특성들의 성능을 최적화함으로써 HLL이 가장 잘 지원될 수 있다.
- RISC 구조는 크게 다음과 같은 세 가지 요소들에 의하여 특성이 결정될 수 있다.
  1. 많은 수의 레지스터들을 사용하거나, 레지스터 용도를 최적화하기 위해서 컴파일러를 이용한다.(Memory Access, Loop, Call 최적화)
  2. 명령어 파이프라인의 설계에 신중한 주의를 기울인다.(Loop 조심하는 경향)
  3. 명령어들은 예측할 수 있는 비용을 가지고 있어야 하며, 고성능 구현과 일관성이 있어야 한다.(Embedded: 다용성, 다기능, cost, 성능 등)

<br/>
<br/>

## RISC의 큰 레지스터 파일의 사용


















