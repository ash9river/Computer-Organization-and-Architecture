# 프로세서의 조직과 기능

## 프로세서 조직

- 프로세서에게 부과되는 요구 사항
  - `명령어 인출(Fetch Instruction)`
    - 프로세서는 기억장치(레지스터, 캐시, 메인 메모리)로부터 명령어를 읽어온다.
  - `명령어 해석(Interpret Instruction)`
    - 명령어는 수행해야 할 동작을 결정하기 위해 해독(decode)된다.
  - `데이터 인출(Fetch Data)`
    - 명령어를 실행하기 위하여 *기억장치* 또는 *I/O 모듈* 로부터 데이터를 읽어와야 할 수도 있다.
  - `데이터 처리(Process Data)`
    - 명령어를 실행하기 위하여 데이터에 대한 산술적 또는 논리적 연산을 요구할 수 있다.
  - `데이터 쓰기(Write Data)`
    - 실행한 결과로써 데이터를 기억장치 또는 I/O 모듈에 써야할 수 있다.     

<br/>

### 시스템 버스와 접속된 CPU

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/d8475fad-b826-4a76-acb2-c666f9bb7fcb">

<br/>

### CPU의 내부 조직

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/e9aacf68-8af3-4e28-8030-115b6ccc3f0d">

<br/>
<br/>

## 레지스터 조직

- 프로세서 내부에는 그 계층에서 메인 메모리와 캐시보다 위의 레벨에서 기능을 수행하는 레지스터 집합이 존재한다.
- 프로세서 내의 레지스터들은 두 가지 역할을 수행한다.
  - 사용자에게 보이는 레지스터들(User Visible->SW 개발자)
    - *기계어* 혹은 *어셈블리어* 프로그래머로 하여금 레지스터들의 사용을 최적화함으로써 메인 메모리의 사용을 최소화한다.
  - 제어 및 상태 레지스터들
    - 프로세서의 동작을 제어하는 제어 유닛과 프로그램의 실행을 제어하는 `운영체제(OS)` 프로그램에 의해 사용된다.
   
> System : OS or administrator
> User : Software Developer

### 사용자에게 보이는 레지스터들(User-Visible Registers)

- 프로세서가 실행하는 기계어에 의해 참조된다.
  - `일반 목적용(General-Purposed) 레지스터들` : 프로그래머에 의하여 여러 가지 용도로 배정될 수 있다.
  - `데이터 레지스터들` : 데이터 저장에만 사용될 수 있으며, 오퍼랜드의 주소를 계산하는데 사용될 수 없다.
  - `주소 레지스터들` : 대체로 일반 목적용으로 사용된다. 세그먼트 포인터, 인덱스 레지스터, 스택 포인터 등이 있다.
  - `조건 코드들` : 플래그(flag)라고도 하고, 연산의 결과로서 프로레서에 의해 세트된다(Read-Only).

### 조건 코드들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/71f3e01a-ce9e-4558-9cba-432dc818843c">

<br/>

### 제어 및 상태 레지스터들

- `프로그램 카운터(PC)` : 인출할 명령어의 주소를 가지고 있다.
- `명령어 레지스터(IR)` : 가장 최근에 인출한 명령어를 가지고 있다.
- `기억장치 주소 레지스터(MAR)` : 기억장치 내 어떤 위치의 주소를 가지고 있다.
- `기억장치 버퍼 레지스터(MBR)` : 기억장치에 쓰여질 데이터 단어 혹은 가장 최근에 읽은 단어를 가지고 있다.

> 💡 네 개의 레지스터들이 명령어 실행을 위해서 반드시 필요하다.

<br/>
<br/>

## 프로그램 상태 단어(Program Status Word)

- 상태 정보를 저장하는 레지스터 혹은 레지스터 세트
- 공통적으로 가지고 있는 필드 혹은 플래그
  - `부호(Sign)`
  - `영(Zero)`
  - `올림수(Carry)`
  - `동등(Equal)`
  - `오버플로우(Overflow)`
  - `인터럽트 가능/불가능(Interrupt Enable/Disable)`
  - `슈퍼바이저(Supervisor)`

> 🎆 정보를 피난시키는데 오래 걸려서 사용한다
> 🎇 PSW를 사용하지 않으면 가상 메모리를 사용할 수 없다.

<br/>
<br/>

### 마이크로 프로세서 레지스터 조직의 예

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/99663537-e8da-4dbe-8ac0-d7d3582417f7">

<br/>
<br/>

## 명령어 사이클

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/baeb82f1-e4b6-41c8-895a-843c852e8c18">

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/13f5959f-b1b0-458f-99d3-50a9f4346ad4">

<br/>
<br/>

## 데이터 흐름

### 인출 사이클

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/94b712c8-d4e5-4110-8f7f-01d16ba0998a)">

<br/>

### 간접 사이클

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/83dbbfb3-d8bd-4f60-9c8b-e51d3ed96bd2">

<br/>


### 인터럽트 사이클

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/9fd86bac-a54c-47d5-832b-166fda8c3fe6">

<br/>
<br/>

## 파이프라인 기법

- CPU의 사용을 극대화하기 위해 명령어를 겹쳐서 실행하는 방법으로, 하나의 코어에 여러 개의 스레드를 사용하는 것이다.
- 제조 공장의 조립 라인을 사용하는 것과 유사하다.
- 새로운 입력이 한쪽 끝으로 들어오고 있을 때, 동시에 다른 끝으로는 먼저 들어온 입력이 출력되어 나간다.
- 이 개념을 명령어 실행에 적용시키기 위해서 명령어도 사실상 여러 개의 단계들을 가지고 있다는 점을 인식해야 한다.
 
<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/1b15b8ef-bff6-4c96-9e1a-f9f1aff435e4">

### 추가적인 단계

1. `명령어 인출(Fetch Instruction)`
    - 다음 명령어를 읽어서 버퍼에 넣는다.
3. `명령어 해독(Decode Instruction)`
    - 연산 코드와 오퍼랜드 지정자들(operand specifiers)을 결정한다.
1. `오퍼랜드 주소의 계산(Calculate Operands)`
    - 각 오퍼랜드의 유효 주소를 계산한다.
    - 변위(displacement), 레지스터 간접 또는 다른 형태의 주소 계산들이 포함될 수 있다.
2. `오퍼랜드 인출(Fetch Operand)`
    - 기억장치로부터 각 오퍼랜드를 인출한다.
    - 레지스터에 있는 오퍼랜드들은 인출할 필요가 없다.
3. `명령어 실행(Execute Instruction)`
    - 지정된 연산을 수행하고, 그 결과를 지정된 목적지 오퍼랜드 위치에 저장한다.
1. `오퍼랜드 저장(Write Operand)`
    - 결과를 기억장치에 저장한다.

<br/>
<br/>

## 명령어 파이프라인 연산

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/549467e6-ec20-43cc-b341-3ab3926a563a">

<br/>

### 6단계 명령어 파이프라인

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/be468a34-f73c-483a-98fb-2b72452d5945">

<br/>

### 파이프라인의 다른 표현

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/0943e61d-7071-49d5-a66e-88983c91f57e">

<br/>

### 명령어 파이프라이닝에 따른 속도 향상

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/db64a304-2e8b-490e-a6b3-7672fd683342">

<br/>
<br/>

## 파이프라인 해저드


- 명령어의 조건들이 파이프라인 실행을 계속하는 것을 허용하지 않게 만듦으로써  파이프라인 전체 또는 일부가 멈출 때(stall), 해저드가 발생한다.
- 파이프라인 버블(pipeline bubble)이라고도 부른다.
- 세 가지 유형의 해저드
  - `자원(resourece)`
  - `데이터(data)`
  - `제어(control)`

### 자원 해저드(Resource Hazard)

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/795e3c20-6df3-4301-a8de-7a26ef40129f">

- 자원 충돌 : 하드웨어가 여러 명령들의 수행을 지원하지 않기 때문에 발생한다.
- 폰노이만 구조 : 프로세서의 구조적인 이유때문에 실행이 불가하다.

<br/>

### 데이터 해저드
    
<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/51462512-a686-4fbf-97e0-2937dbb247ce">

- 앞에 실행될 명령어의 결과가 다음 명령어에 이어서 사용되야 해서 발생되는 문제
- 이 이미지는 RAW(Read After Write), 이전 명령어가 저장한 연산 결과를 후속 명령어가 읽어야할 때, 발생하는 데이타 해저드의 상태도를 나타낸다. 

<br/>

### 데이터 해저드의 유형들

- `


















