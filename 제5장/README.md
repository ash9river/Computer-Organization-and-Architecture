# 제 5장 내부 기억장치

## 기억 소자(Memory Cell)의 동작과 반도체 기억장치의 유형

![KakaoTalk_20231022_180545996](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/2d164700-a2ab-455e-a515-6f5a02e3d378)

<br/>
<br/>

## DRAM 조직과 SRAM 조직

![KakaoTalk_20231022_180545996_01](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/aaa8438e-d9c4-4d79-abe7-2fad09d425d1)

<br/>

### Static RAM(SRAM)

- 프로세서에서 사용되는 것과 같은 논리 소자를 이용하는 디지털 장치
- 이진수를 전통적인 플립-플롭 논리 게이트들을 이용하여 저장
- 전력이 공급되는 동안에는 데이터 계속 유지
<br/>

## SRAM vs DRAM

- 모두 휘발성
  - 데이터 유지를 위해서는 전력이 계속 공급되어야함.
- 동적 소자(Dynamic Cell)
  - 만들기 쉽고 더 작고 더 저렴하다.
  - 재충전 회로 필요
  - 대용량 기억장치 요구에 부함하여 메인 메로이로 사용
- 정적 소자(Static Cell)
  - 더 빠름
  - 캐시 메모리로 사용(on Chip & off Chip Cache 둘다)
 
<br/>
<br/>

## 읽기 전용 기억장치(Read Only Memory:ROM)

- 변경될 수 없는 데이터를 저장하는 데 사용
- 전력을 주기적으로 공급하지 않아도 비트값이 기억장치에서 유지된다.
- 데이터 혹은 프로그램이 메인 메모리에 영구 저장되므로(ex: BIOS) 서브 메모리에서 옮겨올 필요가 없다.
- 제조 과정에서 데이터들의 실제 선들의 접속을 통하여 칩 속에 내장됨
-  단점
  - 데이터를 삽입하는 과정에서 비교적 높은 고정 비용이 든다.
  - 한 비트 오류 발생하면 모든 ROM을 폐기해야 한다.
  
<br/>

## Programmable ROM(PROM)

- 버려지는 비용을 따졌을 때 더 저렴하다
- 비휘발성이며 한번만 쓰여질 수 있다.
- PROM에서 데이터를 쓰는 것이 전기적으로 가능해서, 제조가 완료되고도 공급자 또는 사용자가 임의로 쓸 수 있다.
- 쓰기 과정을 위하여 특수 장치가 필요하다. (EPROM : UV)

<br/>

## Read-Mostly-Memory

- `EPROM`
  - UV 장치, chip 단위 삭제
  - 삭제 및 프로그래밍 가능한 ROM
  - 삭제 과정 반복 가능
- `EEPROM`
  - Electrically, byte 단위 삭제
  - 전기적으로 삭제 가능한 ROM
  - 쓰기 전에 그 이전 내용을 지울 필요 없음
  - 비휘발성, 일반적인 버스 제어, 주소 및 데이터 선들을 이용하여 갱신할 수 있음
- `Flash Memory`
  - block 단위 삭제
  - byte 레벨 삭제는 제공하지 않음
 
<br/>

### 전형적인 16Mb DRAM

![KakaoTalk_20231022_183701186](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/00fa2f65-2530-454b-93c8-bdd8b1888c39)

<br/>
<br/>

## 인터리브드 기억장치(Interleaved Memory)

- DRAM 메모리 칩들의 집합으로 구성
- 여러 개의 칩이 모여 메모리 뱅크(Memory Bank)를 형성
- 각 뱅크는 메모리 읽기 혹은 쓰기 요구를 독립적으로 서비스할 수 있다.
- K 개의 뱅크들을 가진 시스템은 K 개의 요구를 동시에 서비스할 수 있기에 메모리의 속도를 K 배만큼 증가시킬 수 있다.

<br/>

## 오류 정정

- 하드 결함(Hard Failure)
  - 영구적인 물리적 결함
  - 메모리 셀이 안정되게 데이터를 저장할 수 없음
- 소프트 오류(Soft Error)
  - 메모리의 내용이 일시적으로 변경됨

 <br/>
 
## 해밍 오류 정정 코드

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/895acf38-bb89-4596-ae65-b4c9fa8ffa8c">
<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/1434e4c4-7c9f-47f3-8ce4-450ff9e43e1f">
<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/2959f075-0fcd-408d-836f-a14c44deb6aa">
  
<br/>
<br/>

## 첨단 DRAM 조직

- 고성능 프로세서들이 사용되었을 때, 가장 심각한 시스템 병목들 중에 하나는 내부 메인 메모리로 접속되는 인터페이스
- 전통적인 DRAM 칩은 내부 구조와 프로세서의 메모리 버스와 인터페이스때문에 한계를 가지고 있음
- 기본적인 DRAM 구조에 여러 가지 보완이 이루어져서 SDRAM(Synchronous <!--clock--> DRAM)
- SDRAM -> DDR 으로 진화

<br/>

## 동기식 DRAM(SDRAM)

- 가장 널리 사용되고 있는 DRAM 형태들 중 하나
- 외부 클록 신호와 동기화되어 대기 상태 없이 프로세서/메모리 버스의 전속력으로 실행되고, 프로세서와 데이터 교환
- 동기식 액세스를 이용하면 DRAM은 시스템 클록의 제어 하에 데이터를 받고 내보내게 됨
  - 프로세서나 다른 master는 명령어와 주소 정보를 발송하고, DRAM에 의해 래치(latch)된다.
  - DRAM은 일정 수의 클록 이후에 응답한다.
  - SDRaM은 request를 처리하는 동안, master는 안전하게 다른 일을 수행할 수 있다.

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/dd89c4ad-70b8-4c0d-8e17-43eff13f8a95">
<br/>

### SDRAM 읽기 타이밍

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/f96dc227-4d1b-43d0-8e10-205b13dae776">

<br/>
<br/>

## Double Data Rate SDRAM(DDR SDRAM)

- SDARM은 데이터를 버스 클록 사이클 당 한 번씩만 프로세서를 보낼 수 있다.
- Double-data-rate DRAM이라고 불리는 새로운 버전의 DRAM은 데이터를 클록 사이클당 두 번씩 보낼 수 있다.
  - 클록펄스의 상승 에지와 하강 에지에서 보낸다.

<br/>

### DDR SDRAM 읽기 타이밍

<img width="80%" height="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/69b2171e-03b6-455c-ac96-71b484f311b8">

<br/>

![KakaoTalk_20231022_192534602](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/76e6d97a-fdcd-4671-a77e-354146ab2365)

<br/>
<br/>

## Flash Memory

- 내부 메모리 및 외부 메모리 응용 모두를 위하여 사용
- 가격과 기능성 EPROM과 EEPROM의 중간
- 메모리 블록만 삭제 가능, 바이트 단위 삭제 불가능

<br/>

![KakaoTalk_20231022_194326274](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/b071b274-4581-4b88-a700-b38d8fe05253)
![KakaoTalk_20231022_194400092](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/d121bdc5-b264-40f2-9980-7b771349c20e)
![KakaoTalk_20231022_194425798](https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/86f7f2d5-082f-4a47-8278-ee59155f0240)


