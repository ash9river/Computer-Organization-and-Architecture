# 명령어 세트 : 주소 지정 방식과 형식


## 주소 지정 방식(Addressing Mode)

1. `즉시(Immediate)`
  - 명령어가 operand 포함
2. `직접(Direct)`
  - 명령어 주소 = operand 위치
3. `간접(Indirect)`
  - 명령어 주소 = operand 위치를 가르키는 주소
4. `레지스터(Registor)`
  - 명령어의 주소 = 레지스터 번호
5. `레지스터 간접(Registor Indirect)`
  - 명령어의 주소 -> 레지스터 번호 -> operand 주소
6. `변위(Displacement)`
  - 여러 개의 주소 결합(덧셈)을 통한 상대주소 계산
7. `스택(Stack)`
  - CPU가 지정하는 자동 증가 주소(암묵적임)

<br/>

### 주소 지정 방식들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/aeb6eaf4-523b-47dc-a19c-7183970bb3e1">

<br/>

### 기본적인 주소지정 방식들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/c9dbd9d7-a54e-4239-abc9-d7cb1c4803a7">

<br/>
<br/>

## 즉시 주소지정

- 가장 간단한 형태의 **주소** 지정
- 오퍼랜드 = A (주소필드)
- 이 방식은 `상수(constant)`를 정의하여 사용하거나, 변수의 초기 값을 세트하는데 사용한다.
  - 일반적으로 수는 **2의 보수 형태**로 저장한다.
  - 오퍼랜드 필드의 맨 좌측 비트(MSB)가 부호 비트로 사용된다.
- **장점**
  - 오퍼랜드를 인출하거나 기억장치를 참조할 필요가 없어서, **명령어 사이클**에서 하나의 기억장치 사이클 또는 캐시 사이클을 줄일 수 있다.
- **단점**
  - 수의 크기가 주소필드의 크기로 제한된다.
 
> $Instruction(word) = opcode + Address \ Field$













