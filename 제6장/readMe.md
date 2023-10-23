# 제 6장 외부 기억장치(I/O 모듈에 연결된 기억장치)

## 자기 디스크

- 디스크는 자성 물질로 코팅된 서브스트레이트라고 불리는, 비자성 물질로 만들어진 원형 평판
  - 최근에는 유리 서브스트레이트가 소개됨
- read current가 자기저항을 읽고, write currnet가 유도성 쓰기를 함

<br/>

## 디스크 배치

![KakaoTalk_20231023_153538725](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/5c2890a0-8fbc-4294-9c7a-c507237785a6)

<br/>

### 윈체스터 디스크 형식

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/d7d293f6-4657-4eaa-9166-7b9c9e7709ff">

<br/>
<br/>

## 디스크의 특성들

- 고정-헤드 디스크
  - 트랙당 한 개의 읽기-쓰기 헤드
- 이동가능-헤드 디스크
  - 하나의 읽기-쓰기 헤드
- 제거 불가능 디스크
 - 디스크 드라이브 내에 영구히 장착
- 제거 가능 디스크
- 이중-면 디스크
 - 평판의 양면에 자성을 가지고 있는 물질이 코팅

<br/>

## 디스크 헤드 메커니즘

- 읽기와 쓱기를 올바르게 수행하기 위해서는 헤드가 충분한 전자장을 발생시키고, 감지할 수 있어야 한다.
- 헤드는 가늘수록 평판에 더 가깝게 접근해야 한다.
 - 헤드가 좁으면 트랙도 좁아져서 밀도가 증가한다.
- 디스크에 헤드가 가까울수록 불순물이나 결함에 의한 오류 발생 가능성이 더 크다.

<br/>
<br/>

## 전형적인 하드 디스크 파라미터

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/f52edd97-d44a-402d-8c34-43f1f255cf56">

<br/>
<br/>

## 디스크 I/O 전송의 타이밍


<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/3e466926-2e50-477a-b955-617a8fb1283b">

<br/>
<br/>

## 디스크 성능 파라미터들

- 디스크 드라이브가 동작 중일 때 디스크는 일정한 속도로 회전한다.
- 읽기나 쓰기를 하려 할 때는 헤드가 원하는 트랙과 그 트랙 내의 원하는 섹터의 시작점에 위치
- `탐색 시간(seek time)`
  - 이동-헤드 시스템에서 헤드가 원하는 트랙까지 이동하는데 걸리는 시간
- `회전 지연(rootational latency)`
  - 섹터가 헤드에 도달할 때까지 걸리는 시간
- `액세스 시간`
  - 액세스 시간 = 탐색 시간 + 회전 지연
  - 읽거나 쓸 위치를 정하는데 걸리는 시간
- `전송 시간(transfer time)`
  - 헤드가 적절한 위치에 놓이면 읽기/쓰기 동작은 그 섹터가 헤드 밑을 지나가는 동안 수행
  - 이 동작의 데이터 전송 부분에 해당된다.
 
<br/>
<br/>

## RAID(cluster:bank와 유사)

- 7 가지 레벨
- 레벨들은 서로 계층적인 관계를 갖지 않으며, 세가지 공통적인 특징을 공유하는 다른 설계 구조이다.
  1. RAID는 운영체제에 의해 하나의 논리적 드라이브로 보여지는 물리적 디스크 드라이브들의 집합
  2. 데이터는 스트라이핑(striping)으로 알려진 방법으로 배열을 이루고 있는 물리적인 디스크 드라이브들에 분산
  3. 여분의 디스크 용량(redundant disk capacity)은 디스크 오류 발생 시 데이터 복구를 보장하기 위한 패리티 정보를 저장할 때 사용 

<br/>

### RAID 레벨들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/96d00f80-9fc8-4f21-a0a0-259d2b0ad05b">

<br/>

![KakaoTalk_20231023_155714392](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/b7664afc-0f10-4018-90f5-8b8be5496b4f)



