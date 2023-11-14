# 명령어 세트 : 특성과 기능

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


<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/dfb21e25-77c5-418f-bc63-f9975e9ac718">




