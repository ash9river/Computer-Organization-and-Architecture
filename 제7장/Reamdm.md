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

>프로세서에 의해 주소가 지정된 I/O 모듈이 받게 되는 네가지 I/O 명령들

- `제어(Control)`:
  - 주변 장치를 활성화시키고 무엇을 해야하는지 알리는 데 사용 
- `검사(Test)`:
  - I/O 모듈과 주변 장치의 여러 가지 상태 조건들을 검사하기 위하여 사용
- `읽기(Read)`:
  - I/O 모둘이 주변 장치로부터 데이터를 읽어서 내부 버퍼에 저장하도록 지시하는 내용 
- `쓰기(Write)`:
  - 이 명령은 I/O 모듈에게 데이터 버스롭터 데이터(byte or word)를 받은 다음에 주변 장치로 전송하도록 하는 명령
 
### 데이터 블록의 입력을 위한 세가지 기술들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/1aab331c-05a2-461d-9f99-2fb42b68a261">

<br/>
<br/>

## I/O 명령어들

> 💡 프로그램 I/O 방식에서 프로세서가 기억장치로부터 인출하는(fetch) I/O 관련 명령어들과 프로세서가 명령어들을 실행하기 위하여 I/O 모듈로 보내는 I/O 명령들 사이에는 밀접한 관계가 있다.

- 각 I/O 장치들은 고유의 번호 또는 주소를 가진다.
- `기억장치 사상`
    - 기억 장소들과 I/O 장치들이 하나의 주소 공간(address space)를 가진다.
    - 버스에 한 개의 읽기 선(read line)과 한 개의 쓰기 선(write line)만 있으면 된다.

### I/O 사상 요약

- `기억장치-사상 I/O`
  - 기억 장소들과 I/O 장치들이 하나의 주소 공간(address space)를 가진다.
  - I/O 모듈 내의 레지스터들을 기억 장소들과 같이 취급한다.
  - 기억 장치와 I/O 장치들을 액세스 할 떄 동일한 기계 명령어를 사용한다.
    - 기억 장치 주소와 I/O 주소가 임의의 형태로 조합되어 존재한다.
- `고립형 I/O(Isolated I/O)`
  - I/O에 대한 주소 공간이 기억 장치의 주소 공간과 분리된다.
  - I/O 혹은 기억 장치 선택 선들이 필요하다.
  - I/O를 위한 특별 명령어가 필요하다.    

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/052421ae-6ab9-4199-bf13-549b4a609c12">

<br/>
<br/>

## 인터럽트-구동 I/O

- 프로그램 I/O의 문제점은 I/O 모듈이 데이터를 수신 or 송신할 준비가 될 떄까지 프로세서가 오래 기다려야한다.
- 다른 방법으로 프로세서가 모듈에게 명령을 보내고 다른 일을 하는것
- I/O 모듈은 프로세서와 데이터 교환이 준비되면 프로세서에게 인터럽트를 보내서 서비스를 요구
- 프로세서는 그에 따른 데이터 전송을 수행하고, 하던 일로 돌아가 다시 수행

<br/>

### 인터럽트 처리도

![KakaoTalk_20231023_222227599](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/0cf1ecfe-c137-43a3-a898-7e1f561f3754)

<br/>
<br/>

## 설계 이슈들

- 인터럽트 I/O를 구현하는 데 있어서 발생하는 두 가지 설계상의 문제들
  - 많은 수의 I/O 모듈이 있을 때, 인터럽트를 발생한 장치를 어떻게 찾을 것인가
  - 여러 개의 인터럽트들이 발생했을 때, 프로세서는 처리할 인터럽트를 어떻게 결정하는가

<br/>

### 장치 확인 방법

- 다수 인터럽트 선(Multiple Interrupt Line): 잘안쓰임
- 소프트웨어 폴(Software Poll)
- 데이지 체인(Daisy Chain): 하드웨어 폴, 벡터화
- 버스 중재(Bus Arbitration): 벡터화

<details>
  <summray>82C55A가 제어하는 방식</summray>
  
![KakaoTalk_20231023_222724806](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/1473e84a-1330-4e84-8acc-8c7c0330fdbc)
</details>

<br/>
<br/>

## 프로그램 I/O와 인터럽트-구동 I/O의 결점들

1. I/O 전송률은 프로세서가 장치를 검사하고 서비스하는 속도에 의해 제한된다.
2. 프로세서가 I/O 전송 관리를 위하여 많은 시간을 소모한다. 각 I/O 전송을 위하여 많은 명령어가 수행되어야 한다. 

> 💡 대량의 데이터가 이동될 떄는 더 효율적인 기법이 요구된다.
>  > 직접 기억장치 액세스(DMA)

<br/>
<br/>

## DMA

<details>
  <summary>직접 기억 장치 액세스</summary>
  
![KakaoTalk_20231023_223756953](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/7ac56f7b-272f-45bd-ac11-a951d73d7bca)
![KakaoTalk_20231023_223839279](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/46a10c60-8b7e-4355-82e5-e320d18faa76)

</details>
