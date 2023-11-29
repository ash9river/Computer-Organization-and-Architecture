# 컴퓨터 산술

## 산술 논리 연산 장치(ALU)

- 컴퓨터의 한 부품으로서 데이터에 대하여 실제적으로 산술 및 논리 연산을 수행하는 부분
- 컴퓨터 시스템의 다른 모든 요소들, 즉 제어 유닛, 레지스터, 기억장치 및 I/O 장치는 처리될 데이터를 ALU로 가져오거나 그 결과를 다시 내보내는 일을 수행
- ALU를 비롯하여 사실상 컴퓨터의 모든 전자 부품들은 이진수를 저장하고 간단한 부울 논리 연산(Boolean logical opreations)을 수행할 수 있는 간단한 디지털 논리 회로들을 이용하여 만들어졌다.

> 1. CPU는 Control과 Computation을 담당
> 1. ALU가 계산
> 2. 어떤 CPU를 선택할 것인가(Architecture는 같으나, Configuration이 다름)

<br/>

## ALU의 입력 및 출력들

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/667ee0a9-b0cb-433b-9e5a-b12d03b9a5e4">

<br/>
<br/>

## 정수 표현

- 이진수 체계에서 임의의 수는 아래와 같이 표현된다.
  - 0과 1
  - 음수에 대한 마이너스 부호(sign bit)
  - 소수점(period) 혹은 기수점(radix point)
- 컴퓨터의 저장 및 처리 목적을 위해서는, 마이너스 부호와 소수점을 위한 특수 기호들의 이점을 활용할 수 없다.
- 이진 숫자들만 수를 표현하는 데에 사용될 수 있다.

## 부호-크기 표현(Signed-Magnitude Representation)

- 음수를 표현하는 방법은 여러 가지가 있다.
  - 단어(word)의 가장 중요한 맨 좌측 비트(leftmost bit)는 부호 비트(sign bit)로 사용된다.
  - 만약 그 비트가 0이면 양수, 1이면 음수이다.
- 부호-크기(sign-magnitude) 표현은 부호 비트를 사용하는 가장 간단한 표현 형태이다.
- 단점
  - 사칙연산을 수행하는 과정에서 부호와 상대적 크기를 모두 고려해야 한다.
  - 0에 대한 표현이 두 가지이다.

> 이와 같은 단점 때문에 부호-크기 표현은 ALU의 정수 부분을 표현하는 데에 거의 사용되지 않는다.

<br/>
<br/>

## 2의 보수 표현

- 최상위 비트를 부호 비트로 사용한다.
- 연산에 유리하며, 다른 비트들을 해석하는 방법은 부호-크기 표현의 경우와 다르다.

|범위|$-2^{n-1}$ ~ $2^{n-1}-1$|
|:---:|---|
|0의 표현|방법 단 한 가지|
|음수화|양의 정수에 대응되는 각 비트의 불리언 보수를 취하고, 1을 더한다.|
|비트 길이 확장|왼쪽으로 비트를 확장시키고, 그 비트를 sign bit와 같은 비트로 다 채운다.|
|오버플로우 규칙|두 수가 같은 부호이며 오버플로우가 일어나면, 해당 sign bit와 반대되는 부호로 바뀐다.|
|뺄셈 규칙|A-B는 B를 2의 보수를 취하고, A에 더한다.|

<br/>

### 참고자료

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/d8e3176a-60a3-441f-84e3-732deb3bd0a8">

<br/>
<br/>

## 범위 확장

- 비트의 길이를 증가시킴에 따라 표현될 수 있는 수의 범위가 확장됨.
- 부호-크기 표현에서는 단순히 부호 비트를 새로운 제일 좌측 비트 위치로 이동시키고, 그 외의 비트들은 0으로 채운다.
- 2의 보수 표현에서 음의 정수의 범위 확장은 다르다.
  - 부호 비트를 새로운 제일 좌측 비트 위치로 이동시키고, 그 외의 비트들은 부호 비트와 같은 값으로 채운다.(`부호확장`)
  
<br/>
<br/>

## 고정-소수점 표현(fixed-point)

- 이진 소수점(radix point or binary point)이 제일 우측 비트의 우측에 고정되어 있다고 가정
- 프로그래머는 이진 소수점의 위치를 묵시적으로 조정함으로써 이진 소수(binary fraction)들에 대해서도 같은 표현 방법들을 사용할 수 있다.

<br/>
<br/>

## 음수화(Negation)

- 부호-크기 표현에서 정수를 음수로 바꾸는 규칙
  - 정수의 각 비트(부호 비트 포함)에 대하여 불 보수(Boolean Complement)를 취한다.
  - 그 결과를 부호없는 이진 정수로 취급하고 1을 더한다.

|수식|내용||
|---:|---|---:|
|+18|=|00010010|
|비트 단위 보수|=|11101101|
|연산|+|1|
|-18|=|11101110|

- 그 음수화된 수의 음수화는, 다시 원점회귀

|수식|내용||
|---:|---|---:|
|-18|=|11101110|
|비트 단위 보수|=|00010001|
|연산|+|1|
|+18|=|00010010|

- 음수화의 특수 경우
  - `0의 two's complement` 
    - 오버플로우가 무시된다.
  - `-128의 two's complement`
    - 똑같이 -128이 된다. 

## 덧셈

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/19ebc9b7-bff1-4e08-84c2-946d2c0e296c">

## 뺼셈

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/c7d2a7a2-70ad-4d67-af07-072c8523b85a">

<br/>

### 규칙

- `오버플로우 규칙`
  - *Flag 체크* : 두 수들이 더해질 때, 두 수들이 모두 양수이거나, 음수이지만, 결과가 반대의 부호이먄 오버플로우가 발생한 것이다.
- `뺄셈 규칙`
   -  어떤 수(subtrahend)를 다른 수(minuend)에서 빼기 위해서는, 어떤 수(subtrahend)의 two's complement(*Negation*)를 취하고 그 수를 다른 수(minuend)와 더한다.

<br/>
<br/>

## two's complement 기하학적 표현

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/f317d641-4517-4799-b5de-aac78fde70a7)">

<br/>
<br/>

## 덧셈 및 뺄셈을 위한 하드웨어

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/40740a93-8974-4882-b9f6-725c52279b98)">

<br/>
<br/>

## 곱셈

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/93466d5d-b29f-401a-b2b1-7333b5156eba">

<br/>
<br/>

### 보호(Gaurd) 없는 이진 곱셈

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/5d6b00f8-6392-455a-ad95-97a1176c897c">

### 2의 보수 곱셈

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/7352dd8f-5766-4e6b-8efc-96d34ca4fc13">

<br/>
<br/>

## Booth Algorithm

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/c9c37aa2-2eae-498f-b319-89c264122db2">

<br/>
<br/>

## 나눗셈

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/bcf8c748-5082-42d5-904d-02c7d6c605bd">

<br/>
<br/>

### Sign 나눗셈

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/912fc371-a44f-4fea-99df-15d7d8e43e9f">

<br/>
<br/>

## 부동-소수점 표현(Float-Point Representation)

- fixed-point가 컴퓨터에서 사용하기엔 비효율적이라서 나온 표현
- 고정 이진(fixed binary) 혹은 기수 소수점(radix point)이 있다고 가정하면 소수(fraction)도 표현할 수 있다.
- 매우 큰 수와 매우 작은 수는 나타낼 수 없다.
- 매우 큰 두 수의 나눗셈에서 몫의 분수 부분을 잃어버릴 수 있다.

<br/>
<br/>

## 전형적인 32 비트 부동-소수점 형식

<img height="80%" width="80%" src="https://github.com/ash9river/Computer-Organization-and-Architecture/assets/121378532/4137c42a-7df7-403b-9925-ed4be6e1512f">

<br/>
<br/>

## 부동-소수점 가수(Significand)

- 단어의 마지막 부분
- 부동-소수점 수는 여러 가지 방법으로표현 가능하다.

$$
  0.110 \times 2^{5}
$$

$$
  110 \times 2^{2}
$$

$$
  0.0110 \times 2^{6}
$$

- 정규화된 수(normalized number)
  - 가수의 가장 중요한 숫자(most significant digit)가 0이 아닌 값(non-zero)로 표현
$$
  \pm 1.bbbb...b \times  2^{ \pm E}
$$ 


















