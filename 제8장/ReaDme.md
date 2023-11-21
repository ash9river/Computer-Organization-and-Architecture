# 제 8장 운영 체제 지원

## 컴퓨터 하드웨어와 소프트웨어 구조

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/9ee84521-f228-41c9-ad1d-62fc5204df07">

<br/>
<br/>

## 운영 체제 서비스(Operating System Service)

- 가장 중요한 시스템 프로그램
- 하드웨어의 디테일을 프로그래머한테 숨기고, 프로그래머에게 시스템을 이용하여 편리한 인터페이스를 제공
- <details>
    <summary>OS는 전형적으로 이하의 서비스를 제공한다.</summary>

  1. Program Creation
  2. Program Execution
  3. Access to I/O devices
  4. Controlled access to files
  5. System access
  6. Error detection and response
  7. Accounting
  
</details>

<br/>
<br/>

## 인터페이스

-  전형적인 컴퓨터 시스템에 있는 중요한 인터페이스들
    - `ISA(Instruction Set Architecture)` 
    - `ABI(Application Binary Interface)`
    - `API(Application Programming Interface)`
 
<br/>
<br/>

## 운영 체제에 대한 자원 관리자로서의 관점

- OS를 이용함으로써 성능 향상이 있느냐?
    - 모니터링과 권한 컨트롤를 이용하여 성능 향상을 이끌어냄. 

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/2a7ff7e2-9e52-429f-9abc-0308596f958a">

<br/>
<br/>

## 운영 체제의 종류

- `대화형 시스템(Interactive System)`
    - 유저와 프로그래머가 컴퓨터에게 잡(JOB)의 실행이나 트랜잭션(transaction)의 수행을 요구함으로써 상호작용한다.
- `배치 시스템(Batch System)`
    - 컴퓨터 프로그램 흐름에 따라 순차적으로 자료를 처리하는 방식 system의 실행시간을 최대한 정확히 예측하는 장점을 가지고 있다.
    - 하나의 작업이 끝나기 전까지는 다른 작업을 할 수 없다.
    - 시간과 비용을 절감과 업무의 효율성을 향상도 높다.    

<br/>
<br/>

## Early Systems

- no OS 시절에 생기는 문제들
    - 스케쥴링
        - 유저가 시스템을 일찍 종료하면 컴퓨터의 자원이 낭비됨 
    - 셋업 타임
        - 컴파일러$+$소스 프로그램이 메모리에 로딩됨
        - 단일 프로그램을 돌릴 때도 사용되서 낭비됨

<br/>
<br/>

## 메모리 레이아웃

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/6e3fa45b-fd7b-420a-a382-0f790e4a8b31">

<br/>

## 바람직한 하드웨어의 특징들

- `메모리 보호(Memory Protection)`
- `명령어 특권(Privileged Instruction)`
- `타이머`
- `인터럽트`

> OS에 friedly하게 발전

<br/>

### OS를 통하여 발생하는 이득

- 멀티프로그래밍으로 시간 단축

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/7037994e-3b0c-421b-b3d2-ed7f0d03019d">

<br/>
<br/>

## Time Sharing System

- 유저가 직접 컴퓨터와 상호작용할 때 사용한다.
- 프로세서의 시간대가 다른 여러 유저들에 의해 공유된다.
- 여러 유저들이 터미널을 통하여 동시에 시스템에 접속할 때, OS는 각 유저 프로그램들의 실행을 상호 배치한다.

<br/>

### Batch Multiprogramming vs Time Sharing

||Batch Multiprogramming|Time Sharing|
|:---|---|---|
|주 목표|프로세서 활용의 극대화|응답 시간 최소화|
|운영체제에게 특정 작업을 수행하도록<br>지시하는 명령이 발생하는 소스|잡이 언어를 제어한다(JCL)<br>명령이 잡에 의해 제공된다|터미널에 입력되는 명령|


<br/>
<br/>

## 스케쥴링

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/5178a021-edac-4428-a5eb-fee699a4e003">

<br/>
<br/>

## Long-Term 스케쥴링

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/3b963438-9faa-4bf8-a8d4-36708f76eecd">

<br/>
<br/>

## Medium-Term 스케쥴링과 Short-Term Scheduling

- `Medium-Term`
  - 너무 많은 process에 메모리를 할당해서 시스템의 성능이 저하되는 경우, 메모리에 적재된 process의 수를 조절하기 위한 스케줄러.
  - 주로 swapping을 통해 문제를 해결한다.
  - swapping-in decision은 멀티프로그래밍 차수를 관리의 필요성에 기반한다.
  - swapping-in decision은 swapped-out process의 메모리 요구 조건 또한 고려한다.
-  `Short-Term`
   - CPU 스케줄러(CPU Scheduler)라고도 불린다.
   - ready 상태의 process 중에서 어떤 process를 다음 번에 running(실행) 상태로 만들지 결정한다.

<br/>

> 일반적으로 스케줄러라고 하면, 단기 스케줄러를 의미하며 미리 정한 스케줄링 알고리즘에 따라서 CPU를 할당할 process를 선택한다.

<br/>

## 프로세스 모델의 5가지 상태

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/1b0bfa49-7563-4f56-94ca-cbc8d84b7b6e">

<br/>
<br/>

## 프로세스 제어 블록

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/9b761871-374b-40f6-a166-8ef0c2ebc0b5">

<br/>
<br/>

### 스케쥴링 예시

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/51681354-0760-448c-8071-f72844c9fabe">

<br/>
<br/>

## OS의 키 엘리먼트

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/a5002b0c-aece-483a-8d1e-1c6077bb5888">

<br/>
<br/>

## 프로세스 스케쥴링

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/4991c12b-ff73-43f0-813f-e23b8dab3316">


<br/>
<br/>

## 메모리 관리 : 스와핑

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/69f10fa2-2684-4c11-923f-e996df5d9972">

<br/>
<br/>

## 메모리 관리 : 파티셔닝

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/f2c25cf8-b37d-4baa-a53d-fd0cb82e0670">

<br/>
<br/>

## 다이나믹 파티셔닝의 효과

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/cbb3b0cc-2031-4c8e-a5d3-ee00a293a033">


<br/>
<br/>

## 메모리 관리 : 페이징

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/972100f9-e4bc-497f-a970-554d68f915c8">

<br/>
<br/>

## 요구 페이징(가상메모리)

- 프로그램 실행 시 프로세스를 구성하는 모든 페이지를 한꺼번에 메모리에 올리는 것이 아니라 당장 사용될 페이지만을 올리는 방식
- 특정 페이지에 대해 CPU의 요청이 들어온 뒤 해당 페이지를 메모리에 적재한다.
- 필요한 페이지만 메모리에 적재하기 때문에 메모리 사용량이 감소한다.
- 프로세스 전체를 메모리에 올리는 데 소요되는 입출력 오버헤드가 감소한다.
- 사용되지 않는 주소 영역에 대한 입출력이 줄어 응답시간이 줄어든다.
- 시스템이 더 많은 프로세스를 수용할 수 있게 해준다.
- 물리적 메모리의 제약을 벗어날 수 있다.

### 지역성(locality)의 원리

- 동일한 값 또는 해당 값에 관계된 스토리지 위치가 자주 액세스 되는 특성

- 참조지역성의 3가지 기본형 : 시간, 공간, 순차 지역성
  1) 공간(spatial) 지역성 : 특성 클러스터들의 기억 장소들에 대해 참조가 집중적으로 이루어지는 경향 으로, 참조된 메모리의 근처의 메모리를 참조.
  2) 시간(temporal) 지역성 : 최근 사용되었던 기억 장소들이 집중적으로 액세스 되는 경향으로, 참조했던 메모리는 빠른 시간에 다시 참조될 확률이 높다.
  3) 순차(sequential) 지역성 : 데이터가 순차적으로 액세스 되는 경향. 프로그램 내의 명령어가 순차적으로 구성되어있다는 것이 대표적인 경우.

## 반전 페이지 테이블 구조

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/d1fa5a91-d62d-40ef-af81-a042ecdd23ea">

<br/>
<br/>

## Translation Lookaside Buffer(TLB)

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/d0506110-546e-4173-933e-f53a5615b4e2">

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/dbffbf35-3049-48d0-9471-56f98a41ea34">

<br/>
<br/>

## Segmentation

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/cf826c58-f8f2-4d20-9037-60f3a7aae270">

<br/>

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/e43a37ad-9e21-4b32-b07e-68eb4d6a1c14">

<br/>
<br/>

## PLus

<img height="80%" width="80%" src="

<br/>
<br/>


