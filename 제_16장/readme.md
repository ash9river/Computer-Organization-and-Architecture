# 명령어 수준 병렬성과 슈퍼스칼라 프로세서

> 명령어-수준 병렬성 : 소프트웨어(컴파일러) <br/>
> 슈퍼스칼라 프로세서 : 하드웨어(component의 추가 사용) 
> component : 기능블럭(ALU 등)

<br/>

> Multicore software : process 기반 <br/>
> Superscalar : instruction 기반(vector 연산 최적화) <br/>
> Scalar : 단일 변수

<br/>

## 슈퍼스칼라

- 스칼라 명령어(단일 명령어)의 실행 성능을 개선하기 위하여 설계된 기계
- 여러 개의 파이프라인들에서 독립적으로 명령어들을 실행할 수 있는 능력
- 명령어들을 프로그램 순서와 다르게 실행하는 것을 허용함으로써 더 많이 이용

<br/>

### 일반적 스칼라 조직과 비교된 슈퍼스칼라 조직

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/cb3fab26-5f9e-4419-aa63-2ec7222a6803">

<br/>

### 유사 슈퍼스칼라 기계의 속도 향상

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/2d8e960a-68fb-400d-9531-10250bd07f5c">

<br/>

### 스테이지 비교

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/e863468c-6211-460e-9234-1b4abce814f9">

<br/>
<br/>

## 제약 사항들(Constraints)

- `명령어-수준 병렬성(Instruction-level parallelisn)`
  - 프로그램의 명령어들이 병렬로 실행될 수 있는 정도(degree)를 의미한다.
  - 이 병렬성을 최대로 유지하기 위해서 *컴파일러* 에 의한 최적화와 하드웨어 기술이 혼합되어 사용될 수 있다.
- *제약 조건들* - *like pipeline hazard*
  - `데이터 의존성(True data dependency)` : RAW
  - `프로시저 의존성(Procedural dependency)` : if문 같은 branch
  - `자원 충돌(Resource conflicts)`
  - `출력 의존성(Output dependency)` : WAW
  - `반의존성(Anti-dependency)` : WAR

<br/>

### 의존성 효과

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/9e53725a-feac-409d-a6df-28498ef8417a">

<br/>

## 명령어-수준 병렬성과 기계 병렬성(Instruction-Level Parallelism and Machine Parallelism)

> 설계상의 주요 사항들

- `명령어 수준 병렬성(Compiler단)`
  - 일정한 순서로 나열된 명령어들이 서로 독립적이라서 중첩에 의해 병렬로 실행될 수 있는 경우에 존재
- `기계 병렬성(Hardware)`
  - 프로세서가 명령어-수준 병렬성을 활용활 수 있는 능력을 나타내는 척도

> 💡 기계 병렬성은 동시에 인출하여 실행할 수 있는 명령어들의 수(병렬 파이프라인들의 수)와 프로세서가 독립적인 명령어들을 찾기 위하여 사용하는 매커지늠의 속도 및 복잡도(complexity)에 의해 결정된다.

<br/>
<br/>

## 명령어 발송 정책(Instruction Issue Policy)

- `명령어 발송`
  - 프로세서의 기능 유닛에서 명령어 실행이 시작되도록 만드는 과정
- `명령어 발송 정책`
  - 명령어들을 발송하는데 필요한 프로토콜
  - 명령어 발송은 명령어가 파이프라인의 해독 단계로부터 첫번째 실행 단계로 이동할 때 필요한 과정
- 세 가지 유형의 순서 조정(orderings)이 중요하다.
  - 명령어들이 인출되는 순서
  - 명령어들이 **실행**되는 순서
  - 명령어들이 **레지스터**와 기억장치의 내용을 갱신하는 순서
- 슈퍼스칼라의 명령어 발송 정책들은 다음과 같이 구분한다.
  - `순서대로 발송하고 순서대로 종료(in-order issue with in-order completion)`
  - `순서대로 발송하고 순서와 다르게 종료(in-order issue with out-of-order completion)`
  - `순서와 다르게 발송하고 순서와 다르게 종료(out-of-order issue with out-of-order completion)`

<br/>

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/014e949c-0317-45f0-991d-a3d3da474ef8">

<br/>

<details>
  <summary>Out-of-Order</summary>


<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/63c0765b-5610-48d1-ba69-4fe8d6af5788">

<br/>

</details>

<br/>
<br/>

## 레지스터 재명명(Registor Renaming)

> 출력 및 반의존성은 레지스터에 있는 값들이 프로그램 흐릉에 의해 결정되는 값들을 더 이상 반영하지 않기 때문에 발생한다.
> > 파이프라인이 젛지되는 결과를 가져온다.
> > > 레지스터들을 동적으로 할당하여 해결

<br/>

### 레지스터 재명명의 효과

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/7eedb870-7046-49bd-8add-39dc7e226dd9">

<br/>
























