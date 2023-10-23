# 제 7장 입력/출력

## I/O 모듈의 일반적인 모델

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/a043badd-e810-4f4a-a3b8-34f5007f3236">

<br/>

## 외부 장치들

- 외부와 컴퓨터 사이에 데이터를 교환할 수 있는 방법 제공
- I/O 모듈과 연결된 링크를 통하여 컴퓨터와 접속
  - 링크(link)는 I/O 모듈과 외부 장치 사이에 제어, 상태 및 데이터를 교환하는데 사용됨
- 주변 장치(peripheral device)
  - I/O 모듈에 접속된 외부 장치

### 외부 장치 블록 다이어그램

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/8fb7a541-2f94-4448-b623-cffaf5f16ff0">

<br/>
<br/>

## 키보드/모니터

- 컴퓨터와 사용자 간의 상호작용에 이용되는 가장 보편적인 도구
- 사용자는 키보드를 통하여 입력을 제공
- 모니터는 컴퓨터가 제공한 데이터를 디스플레이

<br/>

- `IRA(International Refeerence Alphabet)`
  - 데이터 교환의 기본 단위는 문자(Character)
    - 각 문자는 대응되는 코드를 가지고 있다.
    - 코드의 길이는 7 비트 혹은 8 비트(parity or extended)
    - $2^7$ 가지의 서로 다른 문자 표현 가능
  - 문자의 두 가지 유형
    - 프린트 가능한 문자
      - 알파벳, 숫자, 특수문자 등등
    - 제어 문자(Control characters)
      - 프린팅의 제어 혹은 문자의 디스플레이와 관계 있음
      - 다른 제어 문자는 통신 절차와 관계됨      
- `키보드 코드`
  - 사용자가 키를 누르면 전기적 신호가 발생되며, 이 신호가 변환기(transducer)에 의해 해석되어서 해당 IRA 코드의 비트 패선으로 변환된다.
  - 이 비트 패턴은 컴퓨터 내의 I/O 모듈로 전송
  - 출력 시엔 IRA 코드 문자들이 I/O 모듈로부터 외부 장치로 전송됨
  - 변환기는 이 코드를 해석하고, 해당 문자를 표시하거나 요구된 제어 기능을 수행하기 위해서 출력 장치로 필요한 전자 신호 전송
 
<br/>
<br/>

## I/O 모듈의 기능

- `제어와 타이밍(timing)`: 데이터를 받고 외부로 보낼 때, 시간조정
- `오류 검출`
- `데이터 버퍼링`
- `장치들과의 통신`
- `프로세서와의 통신`: 명령어, 데이터, 상태 보고, 주소 재구성 포함

<br/>

## I/O 모듈의 조직

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/7dff285d-b7f1-47d8-9ce3-34e7f9821e8d">

<br/>
<br/>

## 프로그램 I/O(Programmed I/O)

- I/O 동작에는 세 가지 기술들이 사용될 수 있다.
  - `Programmed I/O`
    - 프로세서와 I/O 모듈 사이에 데이터가 교환된다.
    - 프로세서는 프로그램을 실행함으로써 주변 장치의 상태 감지, 읽기, 혹은 쓰기 명령의 전송, 데이터 전송 같은 I/O 동작들을 직접 제어
    - 프로세서가 I/O 모듈에게 명령을 보낸 후에 I/O 동작이 완료될 때까지 기다려야 한다.
    - 만약 프로세서가 I/O 모듈보다 속도가 빠를 때는 프로세서 시간이 낭비된다.
  - `인터럽트-구동 I/O(Interrupt-driven I/O)`
    - 프로세서가 I/O 명령을 보낸 다음에, I/O 모듈이 그 일을 완료하고 인터럽트를 보낼 때까지 다른 명령어들의 수행을 계속할 수 있다. 
  - `직접 기억 장치 액세스(Direct Memory Access:DMA)`
    - I/O 모듈과 메인 메모리가 프로세서의 개입 없이 데이터를 직접 교환  

<br/>

### I/O 기술들

<br/>

||No Interrupts|Use of Interrupts|
|---|---|---|
|I/O to Memory transfer through processor(CPU 관여)|Programmed I/O|Interrupt-driven I/O|
|Direct I/O to Memory transfer(직접)||Direct Memory Access(DMA)|

<br/>
<br/>

## I/O 명령들

- 프로세서에 의해 주소가 지정된 I/O 모듈이 받게 되는 네가지 I/O 명령들
  1. `제어(Control)`:
      - 주변 장치를 활성화시키고 무엇을 해야하는지 알리는 데 사용 
  2.  `검사(Test)`:










