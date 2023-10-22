# 제 4장 캐시 메모리

## 컴퓨터 기억장치의 주요 특징들

- `지역성`
  - 내부: 신호를 바로 주고 받는.다
  - 외부
- `용량`
  - word vs byte
- `전송 단위`
  - word vs block
- `액세스 방법`
  - 연속적
  - 직접
  - 임의
  - 연관
- `성능`
  - 액세스 시간
  - 사이클 시간
  - 전송률
- `물리적 타입`
  - 반도체
  - 자성
  - etc..
- `물리적 특성`
  - 비휘발성/휘발성
  - 지워질 수 있음/없음
- `조직`
  - 메모리 모듈: package 동작

  <br/>
  <br/>

  ## 기억장치 시스템의 특성

  - `위치(Location)`
    - 기억장치가 컴퓨터의 내부 혹은 외부에 있는지를 가리킴
    - internal memory는 main memory와 동일시되기도 함
    - 프로세서는 자신의 local memory인 레지스터들을 필요로 함
    - 캐시는 다른 형태의 내부 기억장치
    - 외부 기억장치는 디스크나 테이프처럼 프로세서가 I/O controller를 통해 액세스할 수 있는 주변기기로 구성됨
  - `용량(Capacity)`
    - 기억장치에서 용량은 byte 단위로 표현
  - `전송 단위(Unit of Transter)`
    - CPU 기준, word 단위
    - 내부 기억장치에서 전송의 단위는 기억장치 모듈로 들어오거나 나가는 전기적 선로의 수와 같다.
  
<br/>
<br/>

## 데이터를 액세스 하는 방식

- 순차적 액세스: tape
- 직접 액세스: HDD
- 임의 액세스: 반도체,DRAM
- 연관 액세스: 캐시(재사용이 높다)

<br/>
<br/>

## 용량과 성능

- 기억장치의 가장 중요한 두가지 특성
- 세가지 성능 파라미터 사용
 - 액세스 시간
 -  기억장치 사이클 시간
 -  전송률(1/사이클시간)

<br/>
<br/>

## 기억장치

- 데이터 저장의 가장 중요한 물리적 특성들
  - 휘발성 기억장치: 전력 공급이 중단되면 정보가 자연적으로 사라짐
  - 비휘발성 기억장치: 정보가 입력되면, 임의로 바꾸기 전까지 유지됨
  - 반도체 기억장치
  - 삭제불가능 기억장치(ROM)
 
<br/>
<br/>

## 기억장치 계층

<img width="60%" height="60%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/6429adae-788e-4b42-8c2f-925915f03759">

- Inboard memory(Internal)
  - `Registers`
    - CPU와 가까움
  - `Cache`
    - CPU와 Cache의 절반은 CPU 내부에 위치  
  - `Main Memory`
    - 삼성이나 SK에서 만드는 DDR/DRAM
- External: I/O module을 통해 Inboard memory와 상호연결
  - Outboard storage
  - Off-line storage(백업용)

<br/>
<br/>

## Memory

- 3 level: inboard vs outboard vs off-line
- Disk cache

### Performance of Two-Level Memory

<img width="60%" height="60%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/03f103d8-823a-4424-8144-bad7c346f7e2">

- $T_1$ : access time to level 1
- $T_2$ : access time to level 2
- $r$ : Hit ratio(The probability of being in the cache)

 Average access Time $$= r \times T_1 + (1-r) \times (T_1 + T_2) $$

- <details>
  <summary>캐시와 주 기억장치</summary>
  
![KakaoTalk_20231022_145355712](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/6e01f9ee-1b27-4ae6-abe6-6ab22159c087)
![KakaoTalk_20231022_145355712_01](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/e2b38fcd-4332-4669-960d-19d3a54fa2f6)
![KakaoTalk_20231022_145355712_02](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/45bbb680-ac90-4319-a172-831da2de87ae)
![KakaoTalk_20231022_145355712_03](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/2d7a98af-50cd-45cc-9cd6-7f85a64ed98a)
</details>

<br/>
<br/>

## 캐시 주소

- 도서관의 자유석 같은거
- CPU -> Cache 접근할 때, 물리적 주소(Main Memory의 실제 주소)를 사용하는지 혹은 가상의 주소(logical)를 쓰는지
- `가상 기억장치`
  -  주 기억장치 크기에 상관없이 논리적 관점으로 기억장치의 주소 지정
  -  하드웨어 기억장치 관리 유닛(MMU)이 각 가상 주솔르 주 기억장치 내의 물리적 주소로 변환

<br/>

### Physical address vs Logical address

<img src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/89b67c5b-33ce-4cbe-b20a-d346ded3f169" width="80%" height="80%">
<br/>
<br/>

## 사상 함수(Mapping Function)

- 캐시 라인의 수는 주 기억장치 블록의 수보다 적기 떄문에, 주 기억장치 블록을 캐시 라인으로 사상(mapping) 해주는 알고리즘 필요
- 직접 vs 연관 vs 세트연관

<br/>

## 직접 사상 (Direct Mapping)

- $i$ : 캐시의 라인 넘버
- $j$ : 메인 메모리의 블락 넘버
- $m$ : 캐시에 있는 라인의 수
- $i$ = $j$ % $m$
- 요약
  - CPU에서 발생시키는 주소 길이가 A이다.
  - 만약에 1 line = 4 word 이면, $2^2$ word 이므로 word bit = 2 bit이다
  - 전체 주소 A 중에 word 를 제외한 주소가 line 주소(s)가 된다
  - 1 line에 몇개의 word가 들어가냐에 따라 달라진다. 만약 1 line = 8 word이면, $2^3$ word 이므로 word bit = 3이다.
    - s = A - w
  - 주소길이 = s+w 비트
  - 메모리에서 접근 가능한 용량 $2^(s+w)$ word 혹은 byte.
  - 블록 크기(line) = $2^w$ word
  - 주 기억장치 내의 블록들의 수 = $2^s$
  - 캐시 내 라인들의 수 = m = $2^r$
  - 태그의 크기 = s-r 비트
    - CPU의 주소 길이 = 메인 메모리의 주소 길이 s+w
    - 메인 메모리의 line bit = s
    - 캐시의 line bit = r 
    - 식별을 위해 태그의 크기를 s - r
