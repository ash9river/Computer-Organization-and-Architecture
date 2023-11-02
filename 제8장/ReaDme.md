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
