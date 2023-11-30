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















