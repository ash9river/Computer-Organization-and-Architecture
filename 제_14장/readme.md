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
