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

- 오퍼랜드 위치에 대한 액세스의 충들이 있을 때 발생한다.
- 앞에 실행될 명령어의 결과가 다음 명령어에 이어서 사용되야 해서 발생되는 문제
- 이 이미지는 RAW(Read After Write), 이전 명령어가 저장한 연산 결과를 후속 명령어가 읽어야할 때, 발생하는 데이타 해저드의 상태도를 나타낸다. 

<br/>

### 데이터 해저드의 유형들

- `쓰기 후 읽기(Read After Read:RAW)` : 순수 의존성(True Dependency)
  - 어떤 명령어가 레지스터 혹은 기억장치의 데이터를 수정하며, 그 다음 명령어는 그 기억장치 혹은 레지스터의 데이터를 읽는다.
  - 만약, 쓰기 동작이 완료되기 전에 읽기가 수행한다면, 해저드가 발생한다.
- `읽기 후 쓰기(Write After Read:WAR)` : 반 의존성(Anti Dependency)
  - 어떤 명령어가 레지스터 혹은 기억장치로부터 읽으면, 그 다음 명령어는 그 위치에 쓰기를 한다.
  - 만약 읽기 동작이 완료되기 전에 쓰기가 수행된다면, 해저드가 발생한다.
  - > $EAX = EAX + EBX$ <br/>
    > $EBX = EBX + ECX$ <br/>
    > 💡 pipeline의 길이가 일정하지 않으면 발생한다.
- `쓰기 후 쓰기(Write After Write:WAW)` : 출력 의존성(Write Dependency)
  - 두 명령어들이 같은 위치에 쓰기를 한다.
  - 만약 쓰기 동작이 원래의 순서와 반대로 이루어진다면, 해저드가 발생한다.
  - > $EAX = EAX + EBX$ <br/>
    > $EAX = EAX + ECX$ <br/>
    > ex) Variable length instructions 

<br/>

### 제어 해저드

- 분기 해저드(branch hazard)라고도 알려졌다.
- 파이프라인이 분기 예측에서 잘못된 결정을 하였을 때, 발생한다.
- 나중에 버려야 할 명령어들을 파이프라인으로 가져온다.
- 분기의 처리 방법
  - `다중 열(Multiple Stream)`
  - `분기 목적지의 선인출(Prefetch Branch Target)`
  - `루프 버퍼(Loop Buffer)`
  - `분기 예측(Branch Prediction)`
  - `지연 분기(Delayed Branch)`

<br/>

### 다중 열

> 간단한 파이프라인은 분기 명령어에 의한 피해가 발생하는데, 그 이유는 다음 인출을 위하여, 두 명령어들 중에서 한 개를 선택하는 과정에서 잘못된 선택을 할 수 있기 때문이다.
> > 이것을 해결하기 위해서, 파이프라인의 앞부분을 중복시켜서 두 개의 명령어들을 모두 인출하는 방법을 사용한다.
> > > 여러 개의 파이프 라인들이 있을 때는 레지스터와 기억장치에 대한 액세스를 하는 과정에서 경합에 대한 지연이 발생한다. <br/>
> > > 원래의 분기에 대한 판단이 완료되기 전에 다른 분기 명령어가 파이프라인으로 들어올 수 있는데, 그러한 명령어는 각각 별도의 명령어가 필요하여, 비효율적이다.

### 분기 목적지 선인출

- 조건 분기가 인식되었을 때, 분기 명령어의 다음 명령어뿐만이 아니라 분기의 목적지 명령어도 함께 인출하는 방법
- 목적지는 분기 명령어가 실행될 때까지 보관된다.
- 만약 분기가 이루어지는 경우, 목적지의 명렁어가 이미 인출되어 있는 상태가 된다.
  > IBM 360/91이 이 방법을 사용한다.

### 루프 버퍼

- 파이프라인의 명령어 인출 단계(Instruction  Fetch Stage)에 포함되어 있는, 작고 고속인 기억장치로서, 가장 최근에 인출된 n개의 명령어들을 순서대로 저장한다.
- 이점들
  - 선인출을 사용함으로써 루프 버퍼는 현재의 명령어 인출 주소보다 앞에 있는 몇개의 명령어들을 저장하고 있으므로, 순서대로 인출된 명령어들은 기억장치를 액세스 안해도 사용 가능하다.
  - 만약 분기 명령어로부터 몇 칸 앞에 있는 목적지로 분기가 이루어진다면, 그 목적지의 주소가 이미 버퍼에 저장되어 있다.
  - 루프나 반복(iteration)을 처리하는데 적합하다.

> 근본적으로 명령어 전용 캐시와 유사하다. <br/>
> 차이점
> > 루프 버퍼는 명령어들을 순서대로만 저장한다. <br/>
> > 용량이 작고 비용이 저렴하다.

<br/>

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/2b0666b5-0aaa-4ff6-8f0d-dcbdc68f10d9">

<br/>

### 분기 예측

- 분기가 이루어질 것인지 예측하는 데 사용되는 여러 가지 기술들
  - 정적(static)인 방법들 : 조건 분기 명령어가 실행되는 시간까지의 실행 역사(execution history)에 의존하지 않음
    - `Predict Never Taken`
    - `Predict Always Taken`
    - `Predict By Opcode`
  - 동적(Dynamic)인 방법들 : 실행 역사에 의존
    - `Taken/not taken switch)`
    - `Branch History Table`

 <br/>

### 분기 예측 흐름도

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/c7f540ba-aa8d-42b1-92fb-2ff0fc87e559">

<br/>

### 분기 예측 상태 다이어그램

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/8b7d5cd7-5d47-4e4f-954d-0cebe8aa4ae3">

<br/>

### 분기의 처리

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/bbb443bc-a390-49fd-9d1e-521ea3d90f3d">

<br/>
<br/>

## Intel 80486 파이프라이닝

- `인출(IF)`
  - 목적: 오래된 데이터가 명령어 해독기에 의해 사용된 즉시 선인출 버퍼들을 새로운 데이터로 채우는 것
  - 선인출 버퍼들이 채워져있도록 하기 위하여 다른 단계들과 독립적으로 동작한다.
- `해독 단계 1(D1)`
  - 연산 코드와 주소 지정 방식 정보는 모두 D1에서 해독된다.
  - 명령어의 3 바이트가 선인출 버퍼로부터 D1 단계로 패스된다.
  - 그런 다음에 D1 해독기는 명령어의 나머지를 처리하기 위해서 D2 단계를 지정한다.
- `해독 단계 2(D2)`
  - 각 연산 코드를 ALU 제어 신호들로 확장한다.
  - 더 복잡한 주소 지정 방식들의 계산도 제어한다.
- `실행(Execute)`
  - ALU 연산, 캐시 액세스 및 레지스터 갱신을 포함한다.
- `되쓰기(Write Back)`
  - 앞의 실행 단계 동안 수정된 레지스터들과 상태 플래그들을 갱신한다.     

<br/>

### 80486 명령어 파이프라인의 사례

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/b6dfdbe2-199c-4075-8d16-9b8173c8e377">

## 레지스터들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/5926c193-107d-402b-a4b3-01720837fe94">

<br/>

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/df666b5a-f1bd-4d2a-8b83-9c9bda8d7f9b">

<br/>

### MMX 레지스터를 부동-소수점 레지스터로 사상

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/fb05be29-abc4-424c-b2c3-1c1e73b4cc81">

<br/>
<br/>

## 인터럽트 처리

- `인터럽트(Interrupt)`
  - 하드웨어로부터의 신호에 의해 발생되고, 프로그램 실행 중에 임의의 시간에 발생된다.
    - 마스크 가능(Maskable) : 인터럽트 무시 가능
    - 마스크 불가능(Nonmaskable)
- `예외들(Exceptions)`
  - 예외는 소프트웨어에 의해 발생되고, 명령어의 실행에 의해 일어난다.
  - 프로세서-검출 예외들(Processor-Detected Exceptions:FP)
> 인터럽트와 예외들 모두 *handler* 실행, 소프트웨어이므로 시작 주소가 있다. <br/>
> 그 시작 주소를 표로 만든 것이 인터럽트 벡터 표이다.
- `인터럽트 벡터 표`
  - 모든 형태의 인터럽트에는 어떤 번호가 지정되며,
  - 그 번호는 인터럽트 벡터 표 내에서의 인덱스로 사용된다. 

### x86 예외 및 인터럽트 벡터 표

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/bd8efd61-d804-45fd-9cb1-bee66982a62f">

<br/>

## ARM 프로세서

> ARM은 아래와 같은 속성들을 가진 주요 RISC 시스템으로 Memory Access 최소화가 주 목표이다.

- 적절한 수의 균일한 레지스터 배열을 가지고 있는데, 몇몇 CISC 시스템들보다는 더 수가 많지만, 대부분의 RISC 시스템들보단 더 적다.
- 데이터 처리의 *load/store* 모델은 연산들이 레지스터에 있는 오퍼랜드에 대해서만 수행되고, 기억장치에 있는 모든 것들에 대하여 직접 이루어지진 않게 되어 있다
- 연산이 수행되기 전에 모든 데이터들이 레지승터에 적재되어야 한다.
  - 메모리 액세스와 연산이 분리
- 결과 값은 다른 연산에 사용될 수도 있고, 기억장치에 저장될 수도 있다.
- 균일한 고정-길이 명령어를 사용한다.
  - ARM의 표준 세트: 32 비트
  - 섬 명령어 세트(Thumb Instruction Set): 16비트
- 적은 수의 주소지정 방식들을 사용하는데, 모든 *load/store* 주소들은 레지스터들과 명령어 필드에 의하여 결정된다.
  - 기억장치에 있는 값들을 포함하는 간접 혹은 인덱스 주소 지정 방식은 사용되지 않고, 레지스터를 활용한다.
- 자동 증가 및 자동 감소 주소 지정 방식들이 프로그램 루프의 연산을 개선시키기 위해 사용된다.
- 명령어들을 조건부로 실행시킴으로써 조건 분기 명령어의 필요성이 최소화되며, 그에 따른 파이프라인 플러시(flush)가 줄어들기 때문에 파이프라인 효율이 개선된다.

<br/>

### 간략화된 ARM 조직

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/3ad0e8ff-b938-47ac-b126-1bc9c1a6d7be">

<br/>

### 프로세서 모드들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/7f25df79-35d1-4b96-81c8-57e0461dd9ac">

<br/>

### 예외 모드들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/52c944c6-2a59-4ff0-85d3-d65048a86b5f">

<br/>

### ARM CPSR 및 SPSR 형식

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/946227cb-71ff-47b1-ab84-6692dd7a3f5d">












