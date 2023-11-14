# 명령어 세트 : 특성과 기능

## 기계 명령어의 특성

- 프로세서의 연산은 실행하는 명령어들에 의하여 결정하는데 그 명령어를 *기계 명령어* 또는 *컴퓨터 명렁어*라고 불린다.
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
<br/>

## 명령어 표현

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/8c31f0e7-2cc1-44d4-bc66-817dbcb654e5">

- 연산코드(Opcode)들은 니모닉스(mnemonics)라는 약어에 의해 표현된다.
- 오퍼랜드를 기호적으로 표현하는 방식이다.
- 각 기호적 연산 코드는 고정된 2진 표현을 가진다.
  - 프로그래머는 각 기호적 오퍼랜드의 위치를 지정한다.

    
|2진 표현|약어|설명|
|---|---|---|
|0000|ADD|Add|
|0001|SUB|Subtract|
|0002|MUL|Multiply|





 









