ㅌ# 명령어 세트 : 특성과 기능

## 기계 명령어의 특성

- 프로세서의 연산은 실행하는 명령어들에 의하여 결정하는데 그 명령어를 `기계 명령어` 또는 `컴퓨터 명렁어` 라고 불린다.
- 프로세서가 실행할 수 있는 여러 가지 명령어들의 집합을 프로세서의 명령어 세트(Instruction Set)이라고 하며, 그 명령어 세트는 CPU의 특징을 결정한다.
- 각 명령어는 프로세서에 의해 실행되는 데에 필요한 모든 정보를 포함해야 된다.

  <br/>
  <br/>

## 기계 명령어의 요소들

- `연산 코드(Operation Code)`
  - 수행될 연산을 지정한다. 연산은 연산 코드 혹은 *opcode*라고 불리는 2진 코드에 의하여 지정된다. 
- `원천 오퍼랜드 참조(Source Operand Reference)`
  - 각 연산은 그 연산을 위한 입력이 되는 한 개 또는 그 이상의 오퍼랜드를 포함한다. 
- `결과 오퍼랜드 참조(Result Operand Reference)`
  - 연산은 결과를 생성
- `다음 명령어 참조(Next Instruction Reference)`
  - 프로세서에서 현재의 명령어 실행이 완료된 후에 다음 명령어를 인출(Fetch)할 위치를 알려준다.

> 연산 코드와 오퍼랜드 참조는 연산/데이터의 흐름과 관련이 있고, 연산 코드와 다음 명령어 참조는 프로그램의 흐름 제어와 관련이 있다.

<br/>

### 원천 오퍼랜드와 결과 오퍼랜드들의 위치

1. 주 기억장치 혹은 가상 기억장치
2. I/O 장치
  - 만약 기억장치-사상 I/O(Memory-mapped I/O) 방식이 사용되었다면, 또 하나의 메인 메모리 혹은 버츄얼 메모리의 주소가 된다.
3. 프로세서 레지스터
  - 만약 레지스터가 한 개만 있다면 참조는 묵시적으로 되고, 아니면 각 레지스터에 고유한 명칭 혹은 번호가 지정되고, 명령어는 그 레지스터의 번호를 포함해야 한다.
4. 즉시(Immediate)
  - 오퍼랜드의 값은 실행될 명령어 내의 한 필드에 포함된다.

<br/>

### 명령어 사이클 상태 다이어그램

[참고하기](https://github.com/ash9river/Computer-Organization-and-Architecture/blob/main/%EC%A0%9C3%EC%9E%A5/READMD.md#%EC%9D%B8%ED%84%B0%EB%9F%BD%ED%8A%B8%EB%A5%BC-%ED%8F%AC%ED%95%A8%ED%95%9C-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%82%AC%EC%9D%B4%ED%81%B4-%EC%83%81%ED%83%9C%EB%8F%84)

<br/>

## 명령어 표현

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/8c31f0e7-2cc1-44d4-bc66-817dbcb654e5">

<br/>

- 연산코드(Opcode)들은 니모닉스(mnemonics)라는 약어에 의해 표현된다.
- 오퍼랜드를 기호적으로 표현하는 방식이다.
- 각 기호적 연산 코드는 고정된 2진 표현을 가진다.
  - 프로그래머는 각 기호적 오퍼랜드의 위치를 지정한다.

    
|2진 표현|약어|설명|
|---|---|---|
|0000|ADD|Add|
|0001|SUB|Subtract|
|0002|MUL|Multiply|

<br/>

### 명령어의 유형들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/64cf9b23-ff48-4e3a-92f6-1a3b7c061ca5">

<br/>
<br/>

## 주소의 개수

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/af31e886-ca07-4c66-aab2-5f4a01f469c7">

<br/>

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/edbd125d-22e1-4e2d-8878-6521e575f779">

<br/>

## 명령어 세트 설계

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/9a1d1570-64c8-42a6-ab06-dd32d7778187">

<br/>
<br/>

## 오퍼랜드의 유형

- `주소`
- `수`
- `문자`
- `논리 데이터`

<br/>

### 수

- 모든 기계어들은 수치적 데이터 유형ㄷ 포함
- 컴퓨터에 저장된 수는 한계(크기 또는 정확도의 제한)가 있다. (비트제한)
- 컴퓨터에서 사용되는 세 가지 유형의 수치 데이터
  - 2진 정수 or 2진 고정 소수점
  - 2진 부동 소수점
  - 10진수
- 밀접형 10진수(packed decimal)
  - 각 10진 디지트(decimal digit)는 4 비트 코드로 표현 
  - 수들을 표현하기 위하여 4 비트 코드들이 서로 연결되는데, 그것이 항상 8비트의 배수로 이루어진다.

<br/>

### 문자(Character)

- 데이터의 전형적인 한 형태는 문장(text)이나 문자열(character string)
- 문자 데이터가 사람에게 가장 편하지만 데이터 처리 및 통신 시스템에서는 저장 또는 전송이 어렵다.
- 가장 많이 사용되는 문자 코드는 IRA(International Reference Alphabet)
- 저장만 표준을 따르고, 해석은 CPU가 다르게 한다.(아스키 코드의 제어문자)

<br/>

### 논리 데이터

- n 비트 단위를 각 항목이 0이나 1을 가지는 n개의 1 비트 데이터 항목으로 간주한다.(bit 단위 구분 사용)

<br/>

### x86 수치 데이터 유형들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/dfb21e25-77c5-418f-bc63-f9975e9ac718">

<br/>
<br/>

## SIMD(Single-Instruction-Multiple-Data)

- 멀티미디어 응용들의 성능들을 최적화하기 위한 명령어 세트 확장의 일부로 x86 구조에 소개되었다.
- MMX(MultiMedia Extensions)와 SSE(Streaming SIMD Extensions)를 포함한다.
- 데이터 유형들
  - `밀집형 바이트 및 밀집형 바이트 정수` : 8 bytes (64-bit 규격) or 16 bytes (128-bit 규격)
  - `밀집형 단어 및 밀집형 단어 정수` : 4 words (64-bit 규격) or 8 words (128-bit 규격)
  - `밀집형 2중 단어 및 밀집형 2중 단어 정수` : 2 double words (64-bit 규격) or 4 double words (128-bit)
  - `밀집형 4중 단어 및 밀집형 4중 단어 정수` : 2 quad words (128-bit 규격)
  - `밀집형 단일-정밀도 부동-ㅅ소수점 및 밀집형 복수-정밀도 부동-소수점` : 2 single-precision floating-points (64-bit 규격) or 2 double-precision floating-poings (128-bit 규격)

<br/>
<br/>

## ARM 데이터 유형들 

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/84900405-0392-4db8-a20f-548f296366b1">

<br/>

## ARM 엔디언 지원

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/d652f193-3718-4c45-adfd-5e1020f5dc12">

<br/>
<br/>

### 데이터 전송시 반드시 명시해야 할 사항들

- 원천지(source) 및 목적지(destination) 오퍼랜드(operand)의 위치
- 전송될 데이터의 길이
- 오퍼랜드의 주소 지정 방식

<br/>
<br/>
## 연산(Arithmetic)

- 대부분의 컴퓨터들은 덧셈, 뺄셈, 곱셈 및 나눗셈과 같은 기본적인 산술적 연산들을 제공
- 이 연산들은 부호를 가진 정수(고정 소수)를 위하여 제공된다.
- 부동 소수점 수와 밀집형 10진수 제공도 함
- 다른 가능한 연산들을 위한 여러 가지 단일-오퍼랜드 명령어
  - `절대값(Absolute)` : 오퍼랜드의 절대값을 구한다.
  - `음수화(Negate)` : 오퍼랜드를 음수화한다.
  - `증가(Increment)` : 오퍼랜드에 1을 더한다.
  - `감소(Decrement)` : 오퍼랜드에서 1을 뺀다.

<br/>

### 변환(Conversion)

- 연산이 어려움
- Look-Up Table이 필요하다.

<br/>

### 입력/출력

- 여러 가지 방법들이 사용됨
  - `고립형 프로그램 I/O(Isolated Programmed I/O)`
  - `기억장치-사상 I/O(Memory-mapped I/O)`
  - `DMA`
  - `I/O 프로세서의 사용`
 
<br/>

## 시스템 제어(System Control)

- 보통 `System`은 `OS`를 떠올리면 된다.
- 어떤 *특권 상태에서 동작 중이거나*  기억 장치의 *특권 영역 내에 있는 프로그램* 을 수행 중인 동안에만 실행될 수 있는 명령어들
  - 이러한 명령어는 운영 체제의 사용을 위하여 준비되어 있다.
- 시스템 제어 동작들의 예
  - 시스템 제어 명령어는 제어 레지스터의 내용을 읽거나 변경
  - 저장 장치 보호 키(storage protection key)를 읽거나 수정
  - 다중 프로그래밍 시스템에서 프로새서 제어 블록들을 액세스(process 소유권 및 권한 획득)
 
<br/>
<br/>

## 제어의 이동(Transfer of Control)

- 제어의 이동 연산이 필요한 이유들
  - 컴퓨터를 실제로 사용하는데 각 명령어를 한 번 이상, 수천 번 반복하여 실행할 수 있어야 한다.
  - 거의 모든 프로그램들은 어떤 형태의 의사 결정(decision marking)을 포함하고 있다.
  - 전체 프로그램을 여러 개의 작은 조각들로 나누어서 동시에 작성한다.(function 방식)
 
- 가장 일반적으로 볼 수 있는 제어-이동 연산들
  - `분기(branch)`
  - `건너 뜀(skip)`
  - `프로시저 호출(procedure call)` 


<br/>
<br/>

### 내포된 프로시저 구현을 위한 스택의 사용

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/eb86002a-c2df-4a14-9e19-839b1df11155">

<br/>

### 샘플 프로시저를 아용한 스택 프레임의 증가

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/4181a517-882e-4764-8f20-208394ccb085">

<br/>
<br/>

## x86 단일 명령어, 복수 데이터(SIMD) 명령어들

- 1996년에 인텔은 x86 제품에 MMX 기술을 포함
  - `MMX` : 멀티미디어 작업들을 위하여 고도로 최적화된 명령어들의 집합
- 비디오와 오디오 데이터들은 일반적으로 8 비트 혹은 16 비트의 작은 데이터들로 구성된 큰 배열들로 이루어짐
- MMX에서는 세 가지 새로운 데이터 형식들을 정의한다.
  - `밀집형 바이트(Packed byte)`
  - `밀집형 단어(Packed word)`
  - `밀집향 이중단어(Packed double word)`
- 각 데이터 형식은 길이가 64 비트이며, 여러 개의 작은 데이터 필드로 이루어져 있고, 각 필드에는 고정 소수점 정수가 저장되어 있다.





