# 명령어 수준 병렬성과 슈퍼스칼라 프로세서

> Multicore software : process 기반 <br/>
> Superscalar : instruction 기반(vector 연산 최적화) <br/>
> Scalar : 단일 변수

<br/>

> 명령어-수준 병렬성 : 소프트웨어(컴파일러) <br/>
> 슈퍼스칼라 프로세서 : 하드웨어(component의 추가 사용) 
> component : 기능블럭(ALU 등)

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
- *제약 조건들*
  - `데이터 의존성(True data dependency)`
  - `프로시저 의존성(Procedural dependency)`  











