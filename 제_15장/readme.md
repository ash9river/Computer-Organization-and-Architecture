# 축소 명령어 세트 컴퓨터 : RISC

> 들어가기에 앞서, 컴퓨터 조직과 아키텍처의 저자는 CISC보다 RISC가 좀 더 좋다는 편향적인 생각을 가지고 있음을 밝힌다.

## RISC vs CISC  

- *Computer*
  - `CISC(Complex : *intel PC*)` : 복잡한 data access(High Level Language에 최적화)
  - `RISC(Reduced : *ARM*)` : Embedded, Mobile 등 간단한 기기에 맞춰, 단순한 명령어 세트, 단순한 data access

### 몇 가지 CISC, RISC 및 슈퍼스칼라 프로세서의 특징들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/0d170bf9-4824-4524-96ee-5b3281de3e68">

<br/>
<br/>

## 명령어 실행 특성들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/dc138aa2-ad08-4e89-babd-ea214f774425">

<br/>

### HLL 연산들의 상대적 동적 빈도

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/b42c3bee-db67-451c-b081-28ab50776d3c">

<br/>

### 오퍼랜드들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/f9b24018-659d-4347-93ce-41c86b2e7116">

<br/>

### 프로시저 변수들과 지역 스칼라 변수들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/b41a4b04-00d9-45b4-8083-697f0d1baacd">

<br/>

## 제안들(RISC)

- HLL 프로그램에서 가장 많은 시간을 소비하는 특성들의 성능을 최적화함으로써 HLL이 가장 잘 지원될 수 있다.
- RISC 구조는 크게 다음과 같은 세 가지 요소들에 의하여 특성이 결정될 수 있다.
  1. 많은 수의 레지스터들을 사용하거나, 레지스터 용도를 최적화하기 위해서 컴파일러를 이용한다.(Memory Access, Loop, Call 최적화)
  2. 명령어 파이프라인의 설계에 신중한 주의를 기울인다.(Loop 조심하는 경향)
  3. 명령어들은 예측할 수 있는 비용을 가지고 있어야 하며, 고성능 구현과 일관성이 있어야 한다.(Embedded: 다용성, 다기능, cost, 성능 등)

<br/>
<br/>

## RISC의 큰 레지스터 파일의 사용

- 소프트웨어 해결책
  - 컴파일러가 레지스터의 사용 극대화
  - 주어진 시간 내에 가장 많이 사용되는 변수들을 레지스터에 할당
  - 정교한 프로그램 분석 알고리즘 사용
- 하드웨어 해결책
  - 더 많은 레지스터들
  - 더 많은 변수들이 오랜 시간 동안 레지스터에 머무를 수 있게 만든다.
 
<br/>
<br/>

## 중첩 레지스터 윈도우(Overlapping Registor Window)

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/fb2856c2-902b-4504-8a3c-5c62ffe757ce">

<br/>

### 중첩된 윈도우의 순환 버퍼 조직

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/133b2f8d-95db-44dd-8295-bdf4064c599f">

<br/>
<br/>

## 전역 변수들(Global Variables)

- 고급 언어에서 전역(global)로 선언된 변수들에게 컴파일러가 기억장치 내 장소들을 지정할 수 있다.
  - 이 변수들을 참조하는 모든 기계 명령어들은 기억장치-참조 오퍼랜드를 사용한다.
  - 자주 액세스되는 전역 변수들에 대해서는 비효율적이다.
- 다른 방법으로 CPU 내에 전역 레지스터 세트(Global Registor Set)를 둔다.
  - 레지스터들은 수가 고정되어 있고, 모든 프로시저에 의해 이용될 수 있다.
  - 레지스터의 번호를 단순하게 지정하면 명령어 형식이 간단해진다.
- 레지스터들을 서로 다른 주소 지정 방식으로 분리하면 하드웨어에 대한 부담이 늘어난다.

![KakaoTalk_20231202_215131753](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/f2a2c9f7-2c0a-4ba1-924e-544c218de8c3)

### 큰 레지스터 파일 대 캐시 조직의 특성들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/ab9e09da-e46b-4520-aa60-a6c5f467161d">

<br/>

### 스칼라의 참조

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/ff191330-40d2-4f46-82d7-d38a00480ef8">

<br/>
<br/>

## 그래프 컬러링

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/e8eecd03-0d91-4d17-aa6b-79e77f3444f0">

<br/>
<br/>

## 왜 CISC인가?

- 명령어 세트는 점점 명령어의 수가 많아지고 더 복잡해진다.
  - 그 이유들
    1. 컴파일러의 단순화 : C(HLL) -> Compiler -> 기계어
    2. 성능 향상
- 프로그램이 짧아짐에 따른 두가지 이점
  1. 프로그램이 기억장치를 적게 차지하므로 자원(기억장치 공간)이 절약된다.
  2. 성능이 향상된다.
     - 명령어들의 수가 적어지면 인출할 명령어 바이트의 수가 감소한다.
     - 페이징(paging)이 사용될 경우, 짧은 프로그램은 페이지를 적게 차지하므로, 페이지 부재(page fault)가 감소한다.
     - 더 많은 명령어들을 캐시에 적재할 수 있다.

<br/>

### RISC와 비교한 CISC의 상대적 코드 크기

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/ce69328b-e21f-4313-923f-33d0139c554c">

<br/>
<br/>

## 축소 명령어 세트 구조의 특성들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/842c8b8e-fbaa-4443-a20e-524d03a8e924">

<br/>

### 레지스터 간 방식과 기억 장치 간 방식의 비교

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/d91be11d-8fd3-4319-82d6-c7d72f85f0fa">

<br/>

### 몇 가지 프로세서들의 비교

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/ae79728c-2417-4776-8a6b-6df89429f640">

<br/>
<br/>

## 스테이지에 따른 파이프라인의 효과

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/8d7c1703-3f55-4b14-b9ab-a364ddb1b7c2">

<br/>

### 파이프라이닝의 최적화

> 성능 저하의 요인
> > 1. data dependency
> > 2. 불규칙성(branch, loop 등)

- `지연된 분기(Delayed Branch)`
   - 다음 명령어의 실행이 완료될 때까지는 영향을 주지 않는 분기의 이용
   - 분기 바로 다음의 명령어는 지연 슬록(delay slot)이라고 불린다.
 - `지연된 적재(Delayed Load)`
   - 적재의 목표가 되는 레지스터는 CPU에 의해 lock된다.
   - 레지스터를 필요로 하는 명령어를 만나면 CPU는 적재가 완료될 때까지 기다린다.
   - 만약 컴파일러가 명령어를 재배열할 수 있어서 Load 명령어가 파이프라인 내에 있는 동안에 다른 유용한 작업이 처리될 수 있다면, 효율이 높아진다.
 - `루프 언롤링(Loop Unrolling)` : 루프를 풀어 헤친다.
   - 루프의 body를 언롤링 팩터(unrolling factor)라고 불리는 u번만큼 복제한다.
   - 단계 u 반복
   - *성능개선*
     - 루프 오버헤드 줄임
     - 파이프라인 성능을 개선하여, 명령어의 병렬성을 높임
     - 레지스터, 데이터 캐시 or TLB의 지역성 개선
    
> loop 100번, 이하의 코드 실행시 <br/>
> $A[i] = B[i] + C[i]$ <br/>
> 다음과 같이 변경하면, loop 50번 실행 가능 <br/>
> $A[2i] = B[2i] + C[2i]$ <br/>
> $A[2i+1] =B[2i+1]+C[2i+1]$

<br/>

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/6024dfa2-2b32-4788-a127-6eae729928f9">

<br/>

### 정상 및 지연된 분기


<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/bf917549-9459-4921-9217-fa5be488e7ed">

<br/>
<br/>

## MIPS

![KakaoTalk_20231204_180823141](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/f141a4e4-ba72-4af4-b260-c4300b734e8e)
![KakaoTalk_20231204_180847641](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/526a8f3f-35df-4acb-bf40-9d0c8582f991)
![KakaoTalk_20231204_180914412](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/324ffbd1-b0fb-42d1-8bcb-08c98f75eeb5)











 













