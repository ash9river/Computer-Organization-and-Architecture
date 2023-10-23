# 제 6장 외부 기억장치(I/O 모듈에 연결된 기억장치)

## 자기 디스크

- 디스크는 자성 물질로 코팅된 서브스트레이트라고 불리는, 비자성 물질로 만들어진 원형 평판
  - 최근에는 유리 서브스트레이트가 소개됨
- read current가 자기저항을 읽고, write currnet가 유도성 쓰기를 함

<br/>

### 디스크 배치

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












