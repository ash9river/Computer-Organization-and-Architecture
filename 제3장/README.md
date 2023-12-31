# 제 3장 최상위에서 본 컴퓨터의 기능 및 상호연결

## 컴퓨터의 구성요소들

- 거의 모든 현대 컴퓨터의 설계는 폰 노이만 구조를 바탕으로 두고 있다.
  - 데이터와 명령어는 읽기와 쓰기가 가능한 기억장치에 함께 저장된다.
  - 기억장치의 내용은 저장된 데이터의 형식에 관계없이 위치에 따라 주소를 지정할 수 있다.
  - 명령어의 실행은 한 개씩 순서대로 진행된다.
- `하드와이어 프로그램(hardwired program)`
  - 여러 부품들을 모아서 필요한 기능을 수행하도록 연결하는 과정
- `소프트웨어`
  - 하드웨어(범용)의 한 부분이 각 명령어를 해석하여 제어신호를 발생
  - 하드웨어를 재구성하는 대신에 새로운 코드들을 제공 
- 하드웨어 vs 소프트웨어
  - 하드웨어에 프로그래밍하면 프로그래밍이 고정된다.
  - 소프트웨어에 프로그래밍하면 프로그래밍을 가변할 수 있다.

### 주요 구성요소들

- CPU
  - 명령어 해석기
  - 일반 목적용 산술 및 논리 기능 모듈
- I/O 모듈
  - `입력 모듈`
    - 임의 형태를 가진 데이터와 명령어들을 받아들이고 시스템에서 사용할 수 있는 내부 신호로 변환해주는 기본요소 포함
  - `출력 모듈`
    - 결과를 보고하는 수단
- Memory   
  - `기억장치 주소 레지스터(MAR)`
    - 다음에 읽거나 쓸 기억 장소의 주소를 지정
  - `기억장치 버퍼 레지스터(MBR)`
    - 기억장치에 저장될 데이터 혹은 기억장치로부터 읽은 데이터를 일시 저장
  - `I/O 주소 레지스터(I/OAR)`
    - 특정 I/O장치를 지정
  - `I/O 버퍼 레지스터(I/OBR)`
    - I/O 모듈과 CPU 사이의 데이터 교환을 위해 사용

<br/>

### 컴퓨터 구성요소의 최상위 레벨

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/1ac1dff2-dcd0-4714-915c-922187559958">

<br/>
<br/>

## 기본 명령어 사이클(intstruction cycle)

<pre>
                    loop
          ↙⬅⬅⬅⬅⬅⬅⬅⬅⬅⬅⬅⬅⬅↖
start->Fetch Next Instruction->Execute Instruction->Halt
</pre>


<br/>

## 인출 사이클(Fetch Cycle)

- 각 명령어 사이클의 시작 단계에서 프로세서는 기억장치로부터 명령어를 인출한다.
- 프로그램 카운터(PC)는 다음에 인출할 명령어의 주소를 가지고 있다.
- 프로세서는 명령어를 인출한 다음에 PC의 내용을 증가시킴으로써 순서대로 다음 명령어를 인출한다.
- 인출된 명령어는 명령어 레지스터(IR)라고 불리는 프로세서 내부 레지스터에 적재된다.
- 프로세서는 명령어를 해석하고 그 결과에 따라 필요한 동작을 수행한다.

<br/>

## 동작 분류

- 동작에 따른 분류 1,2는 데이터 이동, 3은 데이터 가공
  
1. `프로세서-기억장치`
    - 데이터는 프로세서에서 기억장치 or 기억장치에서 프로세서로 전송된다.
2. `프로세서-I/O`
    - 프로세서와 I/O 모듈 사이에 데이터를 전송함으로써 외부로 혹은 외부로부터 데이터가 전송된다.
3. `데이터 처리`
    - 프로세서는 데이터를 가지고 어떤 산술적 혹은 논리적 연산을 수행한다.
4. `제어`
    - 어떤 명령어는 실행 순서를 변경시키기도 한다.
    - 제어 이후 1번으로 루프

  
<br/>
<br/>

## 가상 머신의 특징

- 명령어 포맷
  - 4비트의 Opcode와 12비트의 주소로 총 16비트
- 인티저 포맷
  - 1비트의 부호비트와 15비트의 크기로 총 16비트
- CPU 내부 레지스터
  - `프로그램 카운터(PC)`: 다음에 인출될 명령어의 주소를 가지고 있는 레지스터
  - `명령 레지스터(IR)`: 가장 최근에 인출된 명령어가 저장되어 있는 레지스터.
  - `누산기(AC)`: 데이터를 일시적으로 저장하는 레지스터

### 프로그램 실행 예제

- 비표준 opcode
  - 0001 = Load AC from Memory
  - 0010 = Store AC to Memory
  - 0101 = Add to AC from Memory 
- 메모리에 있는건 Hexa 코드, 첫 숫자는 opcode, 나머지는 address

<details>
  <summary>동작 예시 Flow 따라서 천천히 </summary></summary>

---

- Step 1 (Fetch Cycle)
  - 300 번지의 1940 IR에 저장
  - 1940 = 0001/940 -> Load AC from Memory(940)
    
|주소|메모리||Internal CPU Registor|CPU Registor Data|
|:---|:---|---|---:|---:|
|300|1940||PC|300|
|301|5941||AC|x|
|302|2941||IR|1940|
|940|0003||||
|941|0002||||

<hr/>

- Step 2 (Execute Cycle)
  - IR에 저장된 명렁어 실행 후 PC 증가시킴
  - AC에 0003 저장, PC 300 -> 301

|주소|메모리||Internal CPU Registor|CPU Registor Data|
|:---|:---|---|---:|---:|
|300|1940||PC|301|
|301|5941||AC|0003|
|302|2941||IR|1940|
|940|0003||||
|941|0002||||

<hr/>

- Step 3 (Fetch Cycle)
  - IR에 301 번지 명령어 5941 저장 

|주소|메모리|여백|Internal CPU Registor|CPU Registor Data|
|:---|:---|---|---:|---:|
|300|1940||PC|301|
|301|5941||AC|0003|
|302|2941||IR|5941|
|940|0003||||
|941|0002||||

<hr/>

- Step 4 (Execute Cycle)
  - 5941 = 1010/941 -> Add AC from Memory(2)
  - 3 + 2 실행 후 PC 증가
    
|주소|메모리||Internal CPU Registor|CPU Registor Data|
|:---|:---|---|---:|---:|
|300|1940||PC|302|
|301|5941||AC|0005|
|302|2941||IR|5941|
|940|0003||||
|941|0002||||

<hr/>

- Step 5 (Fetch Cycle)
  - 302 번지 명령어 IR에 저장
  
|주소|메모리||Internal CPU Registor|CPU Registor Data|
|:---|:---|---|---:|---:|
|300|1940||PC|302|
|301|5941||AC|0005|
|302|2941||IR|2941|
|940|0003||||
|941|0002||||

<hr/>

- Step 6 (Execute Cycle)
  - 2941 = 0010/941 -> Storre AC to Memory
  - AC에 있는 값 메모리에 저장 후 PC 증가

 |주소|메모리||Internal CPU Registor|CPU Registor Data|
|:---|:---|---|---:|---:|
|300|1940||PC|303|
|301|5941||AC|0005|
|302|2941||IR|2941|
|940|0003||||
|941|0005||||

</details>


<br/>
<br/>

## 인터럽트의 종류

- 프로그램
  - 명령어 실행 결과로 발생하는 인터럽트 
- 타이머
  - 프로세서 내부의 타이머에 의해 발생하는 인터럽트
- I/O
  - I/O 컨트롤러에 의해 발생하는 인터럽트  
- Hardware failure
  - 파워 부족이나 메모리 패리티 에러로 발생하는 인터럽트

 <br/>

 ### 프로그램 흐름 제어

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/76a5b328-5547-439a-b75e-d7e3558e0f83">

- interrupt handler를 사용하여 인터럽트 발생시 stop & backup -> 인터럽트 수행 -> restore 순차 실행
  - (a) 인터럽트가 없는 경우
    - 1, 2, 3, 4, 5 순차적 실행으로 실행시간이 너무 길다.
  - (b) short I/O wait
    - I/O 대기가 빨리 끝나는 경우, 인터럽트 사용시 효율적
  - (c) long I/O wait
    - I/O 대기가 늦게 끝나도 효율적이다.

 <br/>

## 인터럽트를 포함한 명령어 사이클

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/4381b531-037e-45b5-9ec9-0054793e306a">

<br/>

## 인터럽트를 포함한 명령어 사이클 상태도

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/2bfda5db-d9a4-4f4a-bce6-212c2b2786b0">

 <br/>
 <br/>

 ## 다중 인터럽트

 - 우선순위를 이용햔 인터럽트의 활용
<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/fd7a9758-6d45-49eb-86dc-4fc8e7a2bacc">
<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/9dc897bd-3d34-43f3-90d7-edcefab74bbb">


<br/>
<br/>

## I/O 기능

- I/O 모듈은 프로세서와 직접 데이터를 교환할 수 있다.
- 프로세서는 I/O 모듈에 대하여 데이터 읽기/쓰기를 할 수 있다.
  - 프로세서는 특정 I/O 모듈에 의하여 제어되는 장치를 구분하기 위하여 주소를 사용한다.
  - 기억장치 참조 명령어가 아니라 I/O 명령어를 사용한다.
- I/O 모듈이 기억장치와 직접 데이터를 교환할 수 있도록 허용하는게 바람직하다.
  - 프로세서가 기억장치 읽기/쓰기를 할 수 있는 권한을 부여함으로써 I/O - 기억장치 간 전송이 프로세서 관여없이 실행할 수 있게 된다.
  - 이 동작을 직접 기억장치 액세스(DMA)라고 부른다.

<br/>

### 상호 연결 조직은 아래 유형의 전송을 지원해야 한다.

- `Memory to Processor` : 프로세서는 기억장치로부터 명령어 또는 데이터를 읽는다.
- `Processor to Memory` : 프로세서는 데이터를 기억장치에 저장한다.
- `I/O to Processor` : 프로세서는 I/O 모듈을 통하여 I/O 장치로부터 데이터를 읽는다.
- `Processor to I/O` : 프로세서는 I/O 장치로 데이터를 보낸다.
- `I/O to or from Memory` : I/O 모듈과 기억장치는 프로세서를 통하지 않고, DMA를 이용하여 직접 데이터를 교환한다. 

<br/>
<br/>

## Data Bus

- 데이터 선들은 시스템 모듈들 간에 데이터 이동 경로를 제공
- 선의 수를 데이터 버스의 폭(width)라고 함
- 선의 수는 한번에 정송할 수 있는 비트 수를 결정하는데에 중요한 요소이다.

### 주소 버스

- 데이터의 source나 destination를 지정하는데 사용
- 폭은 시스템의 최대 기억장치 용량을 결정

### 제어 버스

- 데이터 선들과 주소 선들의 사용 제어

<br/>
<br/>

## 버스 상호연결 방식

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/719e072e-1146-462c-a4fb-cceedb0a3b19">

<br/>

- CPU가 Master, 나머지는 Slave
- DMA가 생겨서 DMA가 중재자(Arbiter) 역할을 함
- 버스를 계층적으로 나누기도 함.

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/a720ec3e-faa3-4f8c-bdd5-4a6010b6be1e">

<br/>
<br/>

## 버스 설계의 요소들

- 버스의 타입에 따라
  - Deciated vs Multiplexed
- 중재의 방법에 따라
  - Centralized vs Distribute
- Timing
  - 동기적 vs 비동기적
- 버스 폭
  - Address vs Data
- 데이터 전송 타입
  - Read vs Write vs etc...
 
  <br/>

  ## 버스 동작의 타이밍

  - `동기식`
    - clock cylce이 존재해서 timing을 맞춰서 동작
  - `비동기식`
    - 맞추지 않고 비동기적 동작(Hand Shaking)

<br/>

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/a1732503-7c96-46e6-8092-a6edeef93145">


<br/>
<br/>

## 점대점 상호연결

- Networking하는 것처럼 동작
- 전용선으로의 회귀
- 모든 점 연결 x, 가까운 점들만 1:1 연결
- 중간자가 매개체 연결

<br/>
<br/>

## QPI(Quick Path Interconnection)

- 복합적인 방향 연결(Multiple access 가능)
  - 시스템에 있는 여러 부품들이 쌍으로 각각 전부 연결되어 있음
- 계층적 프로토콜 구조(like switch fabric)
- 패킷화된 데이터 전송

<br/>

### QPI Layer

- Link(Flits): Hand-Shaking
- Physical(Phits): 물리적으로 연결
- 하드웨어는 피지컬 레이어 전체와 링크 레이어 절반

|레이어 1|연결방식|레이어 2|
|---|:---:|---|
|Protocol|<- packet ->|protocol|
|Routing||Routing|
|Link|<-  Flits  ->|Link|
|Physical|<-  Phits  ->|Physical|

<br/>
<br/>

## QPI Link Layer

- 72비트 메세지 페이로드와 8비트의 에러 컨트롤 코드(Cyclic Redundancy Check)
- `flow control`
  - 수신자가 데이터를 받을 상황인지 체크해서 데이터 송수신
- `error control`
  - 비트에서 탐지하고 고친다.

 <br/>

 ### QPI Routing and Protocol Layers

 - Routing Layer
   - 패킷 순회의 경로 결정
 -  Protocol Layer
   - 패킷을 전송의 단위로 정의
   
<br/>
<br/>

## PCI

- PCI는 버스구조
- PCI Express(PCIe)
  - 네트워크 구조

<br/>

## PCIe

- `TLP`: Transacation Layer Packets
- `DLLP`: Data Link Layer Packets
- Physical Layer의 전체와 Data Link Layer의 절반은 하드웨어로 구성
- Physical Layer는 물리적으로 연결

|레이어 1||레이어 2|
|---|---|---|
|Transaction|<- TLP ->|Transcation|
|Data Link|<- DLLP ->|Data Link|
|Physical||Physical|

- PCIe Multilane Distribution에서 128b/130b 같은 것은 encode할때, iming sync를 위해 2비트를 추가했다.
- `Scrambler`: 연속된 비트가 나오지 않게 조정
- `Clock Recovery Circuit`: 패킷이 바뀌는 구간에서 클록 조정

<br/>

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/8cc4632f-28a0-482b-9a30-16d99070a2af">

<br/>
<br/>

## TL supports four address spaces

- 타겟이 무엇인지에 따라 4가지 분류
  - `Memory`
  - `I/O`
  - `Configure`:구성,제어
  - `Message`: 주소가 저장된 데이터가 아니라 제어용
 
<br/>
