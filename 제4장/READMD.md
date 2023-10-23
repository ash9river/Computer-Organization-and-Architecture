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
- 예시
  - 메인 메모리 전체 주소: 24비트
  - line 14 bits, word 2 bits ->tag 8 bits
  - word 2 bits -> 1 line = 4 words
  - line 14 bits -> 16K cache($2^4 \times 2^{10}$)
  - tag 8 bits = 2 Hexa
  - 4 bits = 1 Hexa

<br/>

### 빅팀 캐시

- 직접 사상 캐시에서 같은 line에 사상되는 두 개의 블록들로부터 word를 반복적으로 읽어야 한다면, 그 블록들은 반복적으로 swap되고 결과적으로 hit ratio 감소하게 되는 스레싱(thrashing) 현상 발생
- 휴지통 같은 개념

<br/>

## 완전 연관 캐시

- 다 불러온다~~~ \<under construction/>

## 세트 연관 사상

- 직접 사상 + 연관 사상
- 요약
  - k-way -> $2^n$ 개의 라인
  - $2^r$ line 구성
  - 세트당 line $2^n$ = k
  - 전체 세트의 수 = $2^r/2^n$ = $2^{r-n}$ = $2^d$ -> d 개의 세트 -> d bit
  - 태그 = s - d bit

<br/>
<br/>

## 교체 알고리즘

- 직접 사상에서는 임의의 블록이 들어갈 수 있는 라인이 하나뿐이기에 선택 불가
- 연관 & 세트-연관에서는 교체 알고리즘 필요

### 가장 널리 사용되고 있는 네가지 알고리즘

- `최소 최근 사용(Least Recently Used:LRU)`
  - 가장 효과적
  - 참조되지 않은 채로 가장 오래 있었던 블록을 교체
  - 구현의 단순성으로 가장 널리 사용됨
- `First-In-First-Out(FIFO)`
  - 캐시 내에 가장 오래 머물렀던 블록 교체
  - 라운드-로빈(Round Robin)이나 원형 버퍼 기법으로 쉽게 구현
- `최소 사용 빈도(Least Frequently Used:LFU)`
  - 가장 적게 참조된 블록 교체
  - 각 라인에 카운터를 두어 구현
- `임의(Random)`
  - 간단한 하드웨어로 구현 가능
  - 다른 알고리즘에 비해 약간의 성능 열화 발생

<br/>
<br/>

## 쓰기 정책(Write Policy)

- 언제 메인 메모리로 업데이트할거냐
- 문제점
  - 한개 이상의 장치들이 메인 메모리를 액세스 할 수 있다.
  - 캐시 무효화 발생
- 해결법
  - 원래의 블록이 변경된 적이 없다면 write out 하지도 않고 overwrite 해도 된다.
  - 적어도 한번 이상 쓰기가 수행된 적이 있다면, 새 블록을 가져오기 전에 캐시의 그 라인을 메모리의 블록에 씀으로써, 메인 메모리 갱신

<br/>

## Write Through and Write Back

- `Write Through`
  - 변경되면 바로 쓰기
  - 가장 간단함
  - 모든 쓰기 동작이 캐시만 아니라 메인 메모리도 동시에 이루어짐
  - 메모리 사용량이 많아져서 병목 현상 발생 가능
- `Write Back`
  - 사라질 때 쓰기
  - 메모리에 대해 쓰기 동작 최소화
  - 캐시 내 데이터만 갱신
  - 메인 메모리의 일부가 무효화됨
    - I/O 모듈에 의한 액세스는 캐시를 통함으로 해결
  - 회로가 복잡해지면 병목 현상 발생

<br/>
<br/>

## 라인 크기

- 블록 크기가 증가할수록 locality의 원리에 따라 처음에는 적중률(hit ratio) 증가
  - locality의 원리 : 적정 수준의 원리(과유불급이라 생각해도 됨) 
- 블록이 커지고, 교체되는 정보의 재사용률이 감소할수록 적중률 감소
- 블록이 커질수록 원하는 word가 아닌 word가 같이 읽어지먀, 사용될 가능성도 낮음
- Cache Size 16KB로 고정
  - 1 line = ? word -> line size = 8 B =>$2^3$
  - $\frac{16K}{8}$ = 2K line

<br/>
<br/>

## 다단계 캐시

- 다단계로 캐시 사용
  1. CPU 안의 캐시(on Chip Cache)
  2. 캐시를 여러단으로 두자

<br/>

## 통합 캐시(Unified Cache)와 분리 캐시(Split Cache)

- 분리 캐시가 보편화됨
  - 명령어 전용 캐시
  - 데이터 전용 캐시
  - 두 캐시는 모두 같은 단계에 존재하며, 전형적으로 두 개의 LI 캐시로 존재
- 통합 캐시의 장점
  - 더 높은 적중률
  - 명령어와 데이터 간의 균형 자동으로 유지
  - 단 한 개의 캐시만 설계하고 구현하면 됨
- L1에서는 분리 캐시, 더 높은 레벨에서는 통합 캐시로 가는 경향이 있음
-  분리 캐시의 장점
  - 명령어 인출/해독 유닛과 실행 유닛 간의 캐시로 인한 경합을 없앨 수 있다.(파이프라이닝에서 중요)

     <br/>
 ### Pentium 4 Cache 설계 사례

|고민|해결|모델명|
|---|---|:---:|
|외부 메모리가 시스템 버스보다 느려짐|외부 캐시를 추가함|386|
|프로세서 속도가 증가됨으로써 외부 버스에 병목 현상 발생|외부 캐시를 on chip 캐시로 바꿈(캐시를 CPU 안에 넣음)|486|
|칩에 공간 제한을 걸어서 내부 캐시의 크기가 작음|L2 캐시 추가|486|
|명령어 인출/해독 유닛과 실행 유닛 간의 캐시로 인한 경합 발생|명령어 캐시와 seperate data를 만듬|Pentium|
|프로세서 속도 증가로 인하여 L2 캐시에 병목 현상 발생|L2 캐시도 CPU 안에 넣음(on Chip)|Pentium Pro|
|엄청 큰 데이터를 다룰 때, 캐시의 크기가 너무 작음|L3 캐시 추가 / L3 캐치 on Chip|Pentiurm 3 / Pentium 4|
