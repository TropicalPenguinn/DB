# 데이터베이스 설계와 ER 모델

## 데이터베이스 설계와 ER 모델
데이터베이스 설계는 **개념적 데이터베이스 설계** 와 **물리적 데이터베이스 설계**로 구분

개념적 데이터베이스 설계는 조직체의 **엔티티,관계,프로세스,무결성 제약조건**등을 나타내는 추상화 모델

- 엔티티는 서로 구분이 되면서, 조직체에서 데이터베이스에 나타내려는 객체
- 관계는 두 개 이상의 엔티티들 간의 연관을 나타냄
- 프로세스는 관련된 활동
- 무결성 제약조건은 데이터의 정확성과 비즈니스 규칙을 의미한다

물리적 데이터베이스 설계에서는 물리적인 저장 장치와 접근 방식을 달무

---
**개념적 수준의 모델은 특정 데이터 모델(DBMS)과 독립적으로 응용 세계를 모델링 할 수 있도록 함. 데이터베이스 구조나 스키마를 하향식으로 개발할 수 있기 위한 틀(framework)을 제공함.**

엔티티-관계(ER, Entity-Relationship) 모델 등이 있으며, 개념적인 데이터 모델이 사상될 수 있는 다수의 구현 데이터 모델(implementation data model; 관계 데이터 모델 등)이 존재함.


--- 
## 데이터베이스 설계의 개요
조직체의 운영과 목적을 지원하기 위해 데이터베이스를 생성하는 과정. 응용과 사용자들이 요구하는 데이터, 데이터 간의 관계를 표현하는 것.

**요구사항 분석, 개념적 설계, DBMS의 선정, 논리적 설계,스키마 정제, 물리적 설계와 튜닝 등으로 이루어짐.**
![](https://velog.velcdn.com/images/everyman123/post/46a3a690-83a4-4665-b2f6-7be3f341efb2/image.png)


(1) 요구사항 수집과 분석: 요구사항에 관한 지식을 기반으로 관련 있는 엔티티들, 이들의 애트리뷰트들, 엔티티들 간의 관계 등을 파악함. 또한 데이터 처리에 관한 연산, 연산들의 의미, 접근하는 데이터의 양 등을 분석함.

(2) 개념적 설계: 조직체에서 사용되는 정보의 모델을 구축하는 과정. 사용자들의 요구사항 명세로부터 개념적 스키마가 만들어짐. 엔티티 타입, 관계 타입, 애트리뷰트들을 식별한 후 도메인을 결정하고, 후보 키와 기본 키를 결정함.

(3) DBMS 선정: 기술적 요인(DBMS의 데이터 모델, 인터페이스, 제공되는 서비스 등)과 경제적 요인(구입 비용, 유지 보수 비용 등)을 고려.

(4) 논리적 설계: 선택한 DBMS의 데이터 모델을 사용하여 논리적 스키마(외부 스키마도 포함)를 생성함. 예를 들어, ER 모델로 표현된 개념적 스키마를 관계 데이터 베이스 스키마로 사상함. 또한 더 좋은 스키마로 변환하기 위해서 정규화 과정을 적용함.

(5) 물리적 설계: 요구사항들을 만족시키기 위해 저장 구조와 접근 경로 등을 결정함. 성능상의 주요 기준에는 여러 가지가 있음.

- 응답 시간
- 트랜잭션 처리율
- 전체 데이터베이스에 대한 보고서 생성 시간

(6) 트랜잭션 설계: 요구사항 수집과 분석 후에, 데이터베이스 설계 과정과 별도로 트랜잭션 설계를 할 수 있음. 트랜잭션은 데이터베이스에서 동작할 응용 프로그램(검색, 갱신 등). 데이터베이스 스키마는 트랜잭션에서 요구하는 정보를 포함해야 함.

---
## ER 모델
EER(Enhanced Entity Relationship) 모델이 데이터베이스 설계 과정에 사용될 수 있음. 개념적 설계를 위한 모델로서, 많은 CASE 도구들에서 지원됨. 실세계를 엔티티, 애트리뷰트, 엔티티들 간의 관계로 표현.

**엔티티**는 사람, 장소, 사건등과 같이 독립적으로 존재하면서 고유하게 식별이 가능한 실세계의 객체. 사원처럼 실체가 있는 것, 개념과 같이 추상적인 것이 있음.

**엔티티**들은 엔티티 타입(또는 엔티티 집합)들로 분류됨.

**엔티티 타입**은 동일한 애트리뷰트들을 가진 엔티티들의 틀. 엔티티 타입은 관계 모델 릴레이션의 스키마에 해당.

**엔티티 집합**은 동일한 애트리뷰트들을 가진 엔티티들의 모임. 엔티티 집합은 관계 모델 릴레이션의 인스턴스에 해당.

엔티티 집합과 엔티티 타입을 엄격하게 구분할 필요는 없음. **ER 다이어그램에서 엔티티 타입은 직사각형으로 나타냄.**

![](https://velog.velcdn.com/images/everyman123/post/e5218cab-17e9-4dff-9bb7-f144e94ddd2d/image.png)

---

**강한 엔티티 타입**(정규 엔티티 타입)은 키 애트리뷰트를 사용하여 고유하게 엔티티들을 식별할 수 있는 엔티티 타입.

**약한 엔티티 타입**은 키를 형성하기에 충분한 애트리뷰트들을 갖지 못한 엔티티 타입. ER 다이어그램에서 이중선 직사각형으로 표기.

**약한 엔티티 타입이 식별되기 위해서는 소유 엔티티 타입(owner entity type)이 제공한 키 애트리뷰트를 결합해야함. 약한 엔티티 타입의 부분 키는 점선 밑줄을 그어 표시**
![](https://velog.velcdn.com/images/everyman123/post/b27bfcdc-a54b-449c-ad97-7c37ab3ab4f6/image.png)

---
하나의 엔티티는 연관된 애트리뷰트들의 집합으로 설명됨.

**키 애트리뷰트는 엔티티 타입 내에서 각 엔티티를 고유하게 식별함. ER 다이어그램에서 기본 키에 속하는 애트리뷰트는 밑줄을 그어 표시함.
**

요구사항 명세에서 명사나 형용사로 표현됨. ER 다이어그램에서 타원형으로 나타냄. 애트리뷰트와 엔티티 타입은 실선으로 연결.

(1) 단순 애트리뷰트(simple attribute)는 다른 애트리뷰트로 나눌 수 없는 애트리뷰트. ER 다이어그램에서 대부분의 애트리뷰트는 단순 애트리뷰트.
(2) 복합 애트리뷰트(composite attribute)는 두 개 이상의 애트리뷰트로 이루어진 애트리뷰트.
![](https://velog.velcdn.com/images/everyman123/post/27d110ed-3ec6-4a60-870e-74d4ffb35a4b/image.png)
(3) 단일 값 애트리뷰트(single-valued attribute)는 엔티티마다 하나의 값을 갖는 애트리뷰트(예: 어떤 사원도 두 개 이상의 사원번호를 갖지 않는 것). ER 다이어그램에서 대부분의 애트리뷰트는 단일 값 애트리뷰트.

(4) 다치 애트리뷰트(multi-valued attribute)는 엔티티마다 여러 개의 값을 가질 수 있는 애트리뷰트. ER 다이어그램에서 이중선 타원으로 표현함.
![](https://velog.velcdn.com/images/everyman123/post/4d3212ba-e909-4d31-84ba-b69189b55cd6/image.png)

(5) 저장된 애트리뷰트(stored attribute)는 다른 애트리뷰트와 독립적으로 존재하는 애트리뷰트. ER 다이어그램에서 대부분의 애트리뷰트는 저장된 애트리뷰트 (예: 사원 엔티티 타입에서 사원이름은 다른 애트리뷰트와 독립적).

(6) 유도된 애트리뷰트(derived attribute): 다른 애트리뷰트의 값으로부터 얻어진 애트리뷰트. 릴레이션의 애트리뷰트로 포함시키지 않는 것이 좋음. ER 다이어그램에서 점선 타원으로 표현함.

![](https://velog.velcdn.com/images/everyman123/post/932bc923-a2cc-4bde-863c-ad5fd6f85e47/image.png)

---
**관계는 엔티티들 사이에 존재하는 연관이나 연결로서 두 개 이상의 엔티티 타입들 사이의 사상으로 생각할 수 있음. 요구사항 명세에서 흔히 동사는 ER 다이어그램에서 관계로 표현됨.
**
**
ER 다이어그램에서 다이어몬드로 표기. 관계 타입이 서로 연관시키는 엔티티 타입들을 관계 타입에 실선으로 연결함.
**

![](https://velog.velcdn.com/images/everyman123/post/fbe147e1-8b9f-42c8-ab4c-5ed26035d311/image.png)

---
관계 타입은 관계의 특징을 기술하는 애트리뷰트들을 가질 수도 있음. 이는 키 애트리뷰트를 갖지 않음.
![](https://velog.velcdn.com/images/everyman123/post/6e61e4af-a8b3-4b14-8c69-bbd82be0edc9/image.png)

---
**차수(degree)는 관계로 연결된 엔티티 타입들의 개수를 의미. 흔한 관계는 두 개의 엔티티 타입을 연결하는 2진 관계.
**
![](https://velog.velcdn.com/images/everyman123/post/488dcf6d-1fca-404b-bc9e-8630be2c63e1/image.png)

---
**카디날리티 비율은 한 엔티티가 참여할 수 있는 관계의 수를 나타냄. 관계를 1:1, 1:N, M:N 으로 구분. 카디날리티에 관한 정보는 간선 위에 나타냄.**
![](https://velog.velcdn.com/images/everyman123/post/e67a64fd-759c-4002-adb8-a9603a33633d/image.png)

(1) 1:1 관계: A의 각 엔티티가 정확하게 B의 한 엔티티와 연관되고, B의 각 엔티티가 정확하게 A의 한 엔티티와 연관된 관계.

(2) 1:N 관계: A의 각 엔티티가 B의 임의의 개수의 엔티티와 연관되고, B의 각 엔티티는 정확하게 A의 한 엔티티와 연관된 관계. 실세계에서 흔히 나타나는 관계.

(3) M:N 관계: 한 엔티티 타입에 속하는 임의의 개수의 엔티티가 다른 엔티티 타입에 속하는 임의의 개수의 엔티티와 연관됨.

---
카디날리티 비율의 최소값과 최대값은 ER 다이어그램에서 관계 타입과 엔티티 타입을 연결하는 실선 위에 (min,max) 형태로 표기.

- min은 각 엔티티는 적어도 min번 관계에 참여함을 의미
- max는 각 엔티티는 최대한 max번 관계에 참여함을 의미
- min=0은 어떤 엔티티가 반드시 관계에 참여해야 할 필요는 없음을 의미
- max=*는 어떤 엔티티가 관계에 임의의 수 만큼 참여할 수 있음을 의미
![](https://velog.velcdn.com/images/everyman123/post/84438a58-5354-4d6a-b517-94123d04eece/image.png)

---
역할(role)은 관계 타입의 의미를 명확하게 하기 위해 사용됨. 특히, 하나의 관계 타입에 하나의 엔티티 타입이 여러 번 나타나는 경우에는 반드시 역할을 표기해야 함. 관계 타입의 간선 위에 표시.
![](https://velog.velcdn.com/images/everyman123/post/510b58e2-5063-4e68-b6f4-8710c75c7138/image.png)

---
전체 참여는 어떤 관계에 한 엔티티 타입의 모든 엔티티만 참여하는 것.
부분 참여는 어떤 관계에 한 엔티티 타입의 일부 엔티티만 참여하는 것.
약한 엔티티 타입은 항상 관계에 전체 참여.

전체 참여는 ER 다이어그램에서 이중 실선으로 표시. 카디날리티 비율과 함께 참여 제약조건은 관계에 대한 중요한 제약조건.
![](https://velog.velcdn.com/images/everyman123/post/2fe1a6f1-07a8-4104-831c-ff80efb227a0/image.png)

---
다중 관계: 두 엔티티 타입 사이에 두 개 이상의 관계 타입이 존재할 수 있음.
![](https://velog.velcdn.com/images/everyman123/post/c5b03ff1-5834-41cb-a361-e0f0dec59ef4/image.png)

순환적 관계: 하나의 엔티티 타입이 동일한 관계 타입에 두 번 이상 참여하는 것.
![](https://velog.velcdn.com/images/everyman123/post/89d7ba02-a031-43ba-9a45-0feea89840ac/image.png)

---

- ER 스키마를 작성하기 위한 지침.

  - 다치 애트리뷰트는 엔티티로 분류해야 함
  - 가능한 한 복합 식별자를 피함
- 데이터베이스 설계 과정.
  - 응용의 요구사항을 수집하여 기술
  - 응용과 연관이 있는 엔티티 타입들을 식별
  - 응용과 연관이 있는 관계 타입들을 식별
  - 1:1, 1:N, M:N 관계를 결정
  - 필요한 애트리뷰트들을 식별하고, 각 애트리뷰트가 가질 수 있는 값들의 집합을 식별
  - 기본 키를 식별
  - 응용을 위한 ER 스키마 다이어그램을 그림
  - ER 스키마 다이어그램이 요구사항과 부합되는지 검사
  - ER 스키마 다이어그램을 DBMS이 사용하는 데이터베이스 모델로 변환

---

많은 애트리뷰트가 엔티티 타입에 연결된 다이어그램을 나타내려면 불편하고 공간을 많이 차지하기에 다른 표기법을 사용.

CASE 도구들에서는 새발(crow-feet) 표기법 및 변형들이 흔히 사용됨.
![](https://velog.velcdn.com/images/everyman123/post/c953d671-d48f-491a-8662-d9e3166a01bd/image.png)


---
## ER 스키마를 관계 모델의 릴레이션으로 사상
 
논리적 설계 단계에서는 E R스키마를 관계 데이터 모델의 릴레이션들로 사상함.

ER 스키마에는 엔티티 타입과 관계 타입이 존재하지만, 관계 데이터베이스에는 이들을 구분하지 않고 릴레이션들만 있음.

![](https://velog.velcdn.com/images/everyman123/post/010969ac-07c2-4d4b-967d-000576569658/image.png)


---
ER-관계 사상 알고리즘

- 단계 1: 정규 엔티티 타입과 단일 값 애트리뷰트
  - ER 스키마의 각 정규 엔티티 타입 E에 대해 하나의 릴레이션 R을 생성함
  - E에 있던 단순 애트리뷰트들을 릴레이션 R에 모두 포함시킴
  - E에서 복합애트리뷰트는, 이를 구성하는 단순 애트리뷰트들만 릴레이션 R에 포함시킴
  - E의 기본키가 릴레이션 R의 기본키가 된다.
  ![](https://velog.velcdn.com/images/everyman123/post/61a40bf6-b79f-4c8e-8bda-d6e86115f8b9/image.png)

- 단계 2: 약한 엔티티 타이과 단일 값 애트리뷰트
  - 각 약한 엔티티 타입 W에 대하여 릴레이션 R을 생성
  - W에 있던 모든 단순 애트리뷰트들을 릴레이션 R에 포함시킴
  - 소유 엔티티 타입의 기본 키를 약한 릴레이션 R에 외래키로 포함시킴
  - **릴레이션 R의 기본키는 약한 엔티티 타입의 부분 키와 소유 엔티티 타입에 해당하는 릴레이션을 참조하는 외래키의 조합 (복합키)**
  ![](https://velog.velcdn.com/images/everyman123/post/3cb029a2-4c75-45a4-931f-40691c72f394/image.png)

- 단계 3: 2진 1:1 관계 타입
  - 각 2진 1:1 관계 타입 R에 대하여, R에 참여하는 엔티티 타입에 대응하는 릴레이션 S와 T를 찾음
  - S와 T중에서 한 릴레이션을 선택한다. 만약 S를 선택했다면 T의 기본 키를 S에 외래 키로 포함시킴
  - S와 T중에서 관계 타입에 완전하게 참여하는 릴레이션을 S의 역할을 하는 릴레이션으로 선택함
  - 관계 타입 R이 가지고 있는 모든 단순 애트리뷰트들을 S에 대응되는 릴레이션에 포함시킴
  - 두 엔티티 타입이 관계 타입 R에 완전하게 참옇할 때는 이들을 하나의 릴레이션으로 합칠 수 있음
  ![](https://velog.velcdn.com/images/everyman123/post/eeec7aaa-54cc-41b2-bedd-79fd93cfbe80/image.png)

- 단계 4; 정규 2진 1:N 관계 타입
  - 정규 2진 1:n 관계타입 R에 대하여, N측의 엔티티 타입에 대응되는 릴레이션 S를 찾는다.
  - 1측의 엔티티 타입에 대응되는 릴레이션 T의 기본 키를 릴레이션 S에 외래키로 포함시킴
  - 관계 타입 R이 가지고 있는 모든 단순 애트리뷰트들을 릴레이션 S에 포함시킴
  
- 단계 5: 2진 M:N 관계 타입
  - 2진 M:N 관계 타입 R에 대해서 릴레이션 R을 생성함
  - 참여한 엔티티 타입의 기본 키를 릴레이션 R에 외래키로 포함시킴. 이들의 조합이 릴레이션 R의 기본키가 됨
  - 관계 타입 R이 가지고 있는 모든 단순 애트리뷰트들을 릴레이션 R에 포함시킴
  ![](https://velog.velcdn.com/images/everyman123/post/7e51843e-cbd9-4494-a17f-0d3fdbcd99a5/image.png)

- 6단계: 3진 이상의 관계 타입
  - 3진 이상의 각 관계 타입 R에 대한 릴레이션 R을 생성함
  - 관계 타입 R에 참여하는 모든 엔티티 타입의 기본 키를 릴레이션 R에 외래 키로 포함시킴
  - 관계 타입 R이 가지고 있는 모든 단순 애트리뷰트을 릴레이션 R에 포함시킴
  - 일반적으로 외래 키들의 조합이 릴레이션 R의 기본 키가 됨
  - 카디날리티가 1:N:N이면 카디날리티가 1인 릴레이션의 기본 키를 참조하는 외래 키를 제외한 나머지 외래 키들의 조합이 릴레이션 R의 기본 키가 됨
  ![](https://velog.velcdn.com/images/everyman123/post/033c70bc-53ec-4a0e-a926-bbcdc2413798/image.png)


- 7단계 : 다치 애트리뷰트
  - 각 다치 애트리뷰트에 대한 릴레이션 R을 생성함
  - 다치 애트리뷰트를 릴레이션 R에 포함시키고, 다치 애트리뷰트를 갖는 엔티티 타입이나 관계 타입의 기본 키를 릴레이션 R에 외래 키로 포함시킴
  - 릴레이션의 R의 기본 키는 다치 애트리뷰트와 외래 키의 조합
  ![](https://velog.velcdn.com/images/everyman123/post/d7d02399-8ec4-44d4-b986-41a6640a9c53/image.png)

# 물리적 데이터베이스 설계
## 물리적 데이터베이스 설계
논리적인 설계의 데이터 구조를 보조 기억 장치상의 화일(물리적인 데이터 모델)로 사상함.
예상 빈도를 포함하여 데이터베이스 질의와 트랜잭션들을 분석함.
데이터에 대한 효율적인 접근을 제공하기 위하여 저장 구조와 접근 방법들을 다룸.
특정 DBMS의 특성을 고려하여 진행됨.
질의를 효율적으로 지원하기 위해서 인덱스 구조를 적절히 사용함.

---
## 보조 기억 장치
자기 디스크는 자기 물질로 만들어진 여러 개의 판으로 이루어짐. 판의 각 면마다 디스크 헤드가 있음.

각 판은 트랙과 섹터로 구분됨. 정보는 디스크 표면 상의 동심원(트랙)을 따라 저장됨. 여러 개의 디스크 면 중에서 같은 지름을 갖는 트랙들을 실린더라고 부름.

블록은 한 개 이상의 섹터들로 이루어짐. 디스크에서 임의의 블록을 읽어오거나 기록하는데 걸리는 시간은 탐구 시간(seek time), 회전 지연 시간(rotational delay), 전송 시간(transfer time)의 합.
    ![](https://velog.velcdn.com/images/everyman123/post/7f195860-1394-453f-99a1-b071daf6fbbc/image.png)

---
## 버퍼 관리와 운영체제
디스크 입출력은 컴퓨터 시스템에서 가장 속도가 느린 작업이므로, 입출력 횟수를 줄이는 것이 DBMS의 성능을 향상하는데 매우 중요. 가능하면 많은 블록들을 주기억 장치에 유지하거나, 자주 참조되는 블록들을 주기억 장치에 유지하면 블록 전송 횟수를 줄일 수 있음.

버퍼는 디스크 블록들을 저장하는 데 사용되는 주기억 장치 공간. 버퍼 관리자는 운영체제의 구성요소로서, 주기억 장치 내에서 버퍼 공간을 할당하고 관리하는 일을 맡음.

**운영체제에서 버퍼 관리를 위해 흔히 사용되는 LRU 알고리즘은 데이터베이스를 위해 항상 우수한 성능을 보이지는 않음.**

---
## 디스크 상에서 화일의 레코드 배치

**릴레이션의 애트리뷰트는 고정 길이 또는 가변 길이의 필드로 표현됨.** 연관된 필드들이 레코드가 됨. **릴레이션을 구성하는 레코드들의 모임이 화일이라고 부르는 블록들의 모임에 저장됨.**

![](https://velog.velcdn.com/images/everyman123/post/1fb5dd69-0aa6-4dfd-86f6-52edd28f71d7/image.png)

한 화일에 속하는 블록들이 반드시 인접해 있을 필요는 없음. 하지만, 인접한 블록들을 읽는 경우에는 탐구 시간과 회전 지연 시간이 없으므로, 입출력 속도가 빠름. 블록들이 인접하도록 화일의 블록들을 재조직할 수 있음.
![](https://velog.velcdn.com/images/everyman123/post/387f14e3-ae82-465e-a4ca-fa82f26fb94b/image.png)


- BLOB(Binary Large Object)은 이미지(GIF, JPG), 동영상(MPEG) 등 대규모 크기의 데이터를 저장하는데 사용됨.


- 채우기 인수(fill factor)는 각 블록에 레코드를 채우는 공간의 비율. 레코드가 삽입될 때 기존의 레코드들을 이동하는 가능성을 줄이기 위해 사용됨. 추가 연산이 많은 경우, 적은 채우기 인수를 사용하면 성능이 올라갈 수 있음
![](https://velog.velcdn.com/images/everyman123/post/e6ea3773-25c7-4eff-b59d-b60a2e651976/image.png)

- 화일 내의 클러스터링(intra-file clustering)은 한 화일 내에서 함께 검색될 가능성이 높은 레코드들을 디스크상에서 물리적으로 가까운 곳에 모아두는 것.
![](https://velog.velcdn.com/images/everyman123/post/9a0ba397-a339-47fb-a2f1-8a47aa1c1e9d/image.png)

- 화일 간의 클러스터링(inter-file clustering)은 논리적으로 연관되어 함께 검색될 가능성이 높은 두 개 이상의 화일에 속한 레코드들을 디스크상에서 물리적으로 가까운 곳에 저장하는 것.

![](https://velog.velcdn.com/images/everyman123/post/f43b177f-2c42-475f-8a59-b1446403f578/image.png)


---
## 화일 조직
(1) 히프 파일(heap file; 비순서화일) 일반적으로 레코드들이 삽입된 순서대로 화일에 저장됨.
- 삽입: 새로운 레코드는 화일의 가장 끝에 추가됨
- 검색: 레코드를 찾기 위해서는 모든 레코드들을 순차적으로 탐색해야 함
- 삭제: 레코드를 찾은 후에 삭제함. 삭제된 레코드가 차지하던 공간을 재사용하지 않음 좋은 성능을 유지하기 위해서 히프 화일을 주기적으로 재조직할 필요가 있음.
![](https://velog.velcdn.com/images/everyman123/post/e967be4d-9789-42a4-b145-cfea8d7e526a/image.png)

(2) 순차 화일(sequential file) 레코드들이 하나 이상의 필드 값에 따라 순서대로 저장된 화일. **일반적으로 레코드의 탐색 키(search key) 값의 순서에 따라 저장됨.** 탐색 키는 순차 화일을 정렬하는데 사용되는 필드.

- 삽입: 삽입하려는 레코드의 순서를 고려해야 하기 때문에 시간이 많이 걸림
- 삭제: 삭제된 레코드가 사용하던 공간을 빈 공간으로 남기기 때문에, 주기적으로 순차 화일을 재조직해야 함 기본 인덱스가 순차 화일에 정의되지 않는 한 순차 화일은 데이터베이스 응용을 위해 거의 사용되지 않음.
![](https://velog.velcdn.com/images/everyman123/post/7080eefb-81a5-45df-ace1-fe7ebc05d548/image.png)

---
## 단일 단계 인덱스
인덱스란 탐색키 를 가진 레코드의 빠른 검색을 위해 <탐색키, 레코드 포인터>의 쌍을 관리하는 구조.

인덱스된 순차 화일은 인덱스를 통해서 임의의 레코드를 접근할 수 있는 화일.

단일 단계 인덱스의 각 엔트리는 <탐색키,레코드에대한포인터>. 엔트리들은 탐색 키 값의 오름차순으로 정렬됨.
![](https://velog.velcdn.com/images/everyman123/post/92369b9a-357f-41cf-b295-79dbc478068f/image.png)
인덱스는 데이터 화일과는 별도의 화일에 저장됨. 인덱스의 크기는 데이터 화일의 크기에 비해 훨씬 작음. 하나의 화일에 여러 개의 인덱스들을 정의할 수 있음.

![](https://velog.velcdn.com/images/everyman123/post/7655fb60-93cb-4ce9-be92-8e7e9e1d3d07/image.png)

**인덱스가 정의된 필드를 탐색 키라고부름. 키를 구성하는 애트리뷰트뿐만 아니라 어떤 애트리뷰트도 탐색 키로 사용될 수 있음.**

탐색 키의 값들은 후보 키처럼 각 투플마다 반드시 고유하지는 않음. 인덱스의 엔트리들은 탐색 키 값의 오름차순으로 저장되어 있으므로 이진탐색을 이용할 수 있음.


**탐색 키가 데이터 화일의 기본 키인 인덱스를 기본 인덱스(primary index)라고 부름. 기본 인덱스는 기본 키의 값에 따라 정렬된 데이터 화일에 대해 정의됨.**

**기본 인덱스는 흔히 희소 인덱스**로 유지할 수 있음. 각 릴레이션마다 최대 한 개의 기본 인덱스를 가질 수 있음.
![](https://velog.velcdn.com/images/everyman123/post/eb21e6d2-aaf4-43ae-abb1-78158f6f315e/image.png)

**클러스터링 인덱스(clustering index)은 탐색 키 값에 따라 정렬된 데이터 화일에 대해 정의됨. 각각의 상이한 키 값마다 하나의 인덱스 엔트리가 인덱스에 포함됨.**

범위 질의에 유용. 범위의 시작 값에 해당하는 인덱스 엔트리를 먼저 찾고, 범위에 속하는 인덱스 엔트리들을 따라가면서 레코드들을 검색하면 디스크에서 읽어오는 블록 수가 최소화됨. 어떤 인덱스 엔트리에서 참조되는 데이터 블록을 읽어오면 그 데이터 블록에 들어있는 대부분의 레코드들은 범위를 만족함.

한 화일은 한 가지 필드들의 조합에 대해서만 정렬될 수 있음(보통 기본 키).

**보조 인덱스(secondary index)는 탐색 키 값에 따라 정렬되지 않은 데이터 화일에 대해 정의됨. 보조 인덱스는 일반적으로 밀집 인덱스이므로, 레코드들을 접근할 때 기본 인덱스를 통하는 경우보다 디스크 접근 횟수가 증가할 수 있음.**
![](https://velog.velcdn.com/images/everyman123/post/8da353a8-d770-4294-829f-c75c94efd0cf/image.png)

- 희소 인덱스는 데이터 블록마다 한 개의 엔트리를 갖고, 밀집 인덱스는 레코드마다 한 개의 엔트리를 가짐.

- 레코드의 길이가 블록 크기 보다 작은 일반적인 경우에, 희소 인덱스의 엔트리 수가 밀집 인덱스의 엔트리 수보다 적음.

- 또한, 희소 인덱스는 일반적으로 밀집 인덱스에 비해 인덱스 단계 수가 1정도 적으므로 인덱스 탐색시 디스크 접근 수가 1만큼 적을 수 있음.

- 희소 인덱스는 밀집 인덱스에 비해 모든 갱신과 대부분의 질의에 대해 더 효율적. 그러나, 질의에서 인덱스가 정의된 애트리뷰트만 검색(예: COUNT 질의)하는 경우에는, 데이터 화일을 접근할 필요 없이 인덱스만 접근해서 질의를 수행할 수 있으므로 밀집 인덱스가 희소 인덱스보다 유리.

- 한 화일은 한 개의 희소 인덱스와 다수의 밀집 인덱스를 가질 수 있음.

- 클러스터링 인덱스는 희소 인덱스일 경우가 많으며 범위 질의 등에 좋음. 보조 인덱스는 밀집 인덱스이므로 일부 질의에 대해서는 화일을 접근할 필요 없이 처리할 수 있음.

---
## 다단계 인덱스
인덱스 자체가 클 경우에는 인덱스를 탐색하는 시간도 오래 걸릴 수 있음. 인덱스 엔트리를 탐색하는 시간을 줄이기 위해서 단일 단계 인덱스를 순서 화일로 간주하고, 단일 단계 인덱스에 대해서 다시 인덱스를 정의할 수 있음.

다단계 인덱스는 가장 상위 단계의 모든 인덱스 엔트리들이 한 블록에 들어갈 수 있을 때까지 이런 과정을 반복함. 가장 상위 단계 인덱스를 마스터 인덱스(master index)라고 부름.

마스터 인덱스는 한 블록으로 이루어지기 때문에 주기억 장치에 상주할 수 있음. 대부분의 다단계 인덱스는 B+-트리를 사용.
![](https://velog.velcdn.com/images/everyman123/post/88541bb1-6ab0-4475-b0a4-7bb329421bfa/image.png)


---
CREATE TABLE문에서 PRIMARY KEY절로 명시한 애트리뷰트에 대해서는 DBMS가 자동으로 기본 인덱스를 생성. UNIQUE로 명시한 애트리뷰트에 대해서는 DBMS가 자동으로 보조 인덱스를 생성.

SQL2는 인덱스 정의 및 제거에 관한 표준 SQL문을 제공하지 않음. 따라서, 다른 애트리뷰트에 인덱스를 정의하기 위해서는 DBMS마다 구문이 다른 CREATE INDEX문을 사용해야 함.
```
CREATE INDEX EmpIndex ON EMPLOYEE (DNO, SALARY);

// 이 인덱스는 아래의 질의들에 활용될 수 있음
SELECT * 
FROM EMPLOYEE 
WHERE DNO=3 AND SALARY = 4000000;

SELECT * 
FROM EMPLOYEE 
WHERE DNO>=2 AND DNO <=3 AND SALARY >= 3000000 
AND SALARY <= 4000000;

SELECT * 
FROM EMPLOYEE 
WHERE DNO = 2;

// 위 인덱스는 아래의 질의에는 활용될 수 없음
SELECT *
FROM EMPLOYEE
WHERE SALARY >= 3000000
AND SALARY <= 4000000;
```
인덱스는 검색 속도를 향상시키지만, 인덱스를 저장하기 위한 공간이 필요하고 삽입, 삭제, 수정 연산의 속도는 저하시킴. 소수의 레코드들을 수정하거나 삭제하는 연산의 속도는 향상됨.

릴레이션이 크고, 질의에서 릴레이션의 투플들 중에 일부(예: 2%~4%)를 검색하고, WHERE절이 잘 표현되었을 때 특히 성능에 도움이됨.

---
## 인덱스 선정 지침과 데이터베이스 튜닝
중요한 질의들의 수행 빈도, 중요한 갱신들의 수행 빈도들을 고려하여 인덱스를 선정함.

- 외래 키는 인덱스를 정의할 후보
- 애트리뷰트에 있는 상이한 값들의 개수가 거의 전체 레코드 수와 비슷하고, 애트리뷰트가 동등 조건에 사용된다면 비 클러스터링 인덱스를 생성하는 것이 좋음
- 릴레이션이 크고, 대부분의 질의에서 검색하는 투플이 2%~4%인 경우에는 인덱스를 생성
- 자주 갱신되는 애트리뷰트에는 인덱스를 정의하지 않는 것이 좋음
- 갱신이 빈번한 릴레이션에는 인덱스를 많이 만드는 것을 피함
- 후보 키는 기본 키가 갖는 모든 특성을 갖기에, 인덱스를 생성할 후보
- 인덱스는 화일의 레코드들을 충분히 분할할 수 있어야 함
- 정수형 애트리뷰트에 인덱스를 생성
- VARCHAR 애트리뷰트에는 인덱스를 만들지 않음
- 작은 화일에는 인덱스를 만들 필요가 없음


언제 인덱스가 사용되지 않는가?

- 시스템 카탈로그가 오래 전의 데이터베이스 상태를 나타냄
- DBMS의 질의 최적화 모듈이 릴레이션의 크기가 작아서 인덱스가 도움이 되지 않는다고 판단함
- 인덱스가 정의된 애트리뷰트에 산술 연산자가 사용됨
- DBMS가 제공하는 내장 함수가 집단 함수 대신에 사용됨
- 널 값에 대해서는 일반적으로 인덱스가 사용되지 않음

질의 튜닝을 위한 추가 지침

- DISTINCT절의 사용을 최소화
- GROUP BY절과 HAVING절의 사용을 최소화
- 임시 릴레이션의 사용을 피함
- SELECT * 대신에 SELECT절에 애트리뷰트 이름들을 구체적으로 명시

# 릴레이션 정규화
부주의한 데이터베이스 설계는 데이터 중복을 야기하며 여러가지 갱신 이상(update anomaly)을 유발함

**정규화는 주어진 릴레이션 스키마ㅡㄹ 함수적 종속성과 기본 키를 기반으로 분석하여, 원래의 릴레이션을 분해함으로써 중복과 세 가지 갱신 이상을 최소화함**

## 정규화 개요
- 세가지 갱신
  - 수정 이상 : 반복된 데이터 중에 일부만 수정하면 데이터의 불일치가 발생
  - 삽입 이상: 불필요한 정보를 함께 저장하지 않고는 어떤 정보를 저장하는 것은 불가능
  - 삭제 이상: 유용한 정보를 함께 삭제하지 않고는 어떤 정보를 삭제하는 것이 불가능
  ![](https://velog.velcdn.com/images/everyman123/post/1fd725ac-b0f0-4df3-a68f-334026649029/image.png)

(1) 정보의 중복: 각 사원이 속한 부서 수만큼 동일한 사원의 투플들이 존재하므로, 사원이름,주소 등이 중복되어 저장 공간이 낭비됨

(2) 수정 이상: 어떤 부서의 이름이 바뀔 때, 이 부서에 근무하는 일부 사원 투플에서만 부서이름을 변경하면 데이터 베이스가 불일치 상태에 빠짐

(3) 삽입이상: 어떤 부서를 신설했는데, 아직 사원을 한 명도 배정하지 않는다면 이 부서에 관한 정보를 입력할 수 없음

(4) 삭제 이상: 어떤 부서에 속한 사원이 단 한 명이 있는데, 이 사원에 관한 투플을 삭제하면 이 사원이 속한 부서에 관한 정보도 모두 릴레이션에서 삭제됨

- 정규형의 종류
제 1 정규형, 제 2 정규형, 제 3 정규형, BCNF(Boyce-Codd normal form),제 4 정규형, 제 5 정규형 일반적으로 데이터베이스 응용에서 데이터베이스를  설게할 때 BCNF까지만 고려함

## 함수적 종속성

**함수적 종속성은 릴레이션의 애트리뷰트들의 의미로부터 결정되고 제2 정규형부터 BCNF까지 적용됨**

**릴레이션 스키마에 대한 주장이지**, 릴레이션의 특정 인스턴스에 대한 주장이 아님, **릴레이션의 모든 인스턴스들이 만족해야 함.**

---
**어떤 애트리뷰트의 값은 다른 애트리뷰트의 값을 고유하게 결정할 수 있음** 
**결정자**는 주어진 릴레이션에서 다른 애트리뷰트들을 고유하게 결정하는 하나 이상의 애트리뷰트. 이때 "A가 B를 결정한다 또는 A가 B의 결정자이다"라고 말한다. A->B
![](https://velog.velcdn.com/images/everyman123/post/2afaa43f-1190-4421-9d64-28becd5cfe6a/image.png)

---
애트리뷰트 A가 애트리뷰트 B의 결정자이면 B가 A에 함수적으로 종속한다고 말함. 즉 A값에 대해 반드시 한 개의 B값이 대응된다는 것.
![](https://velog.velcdn.com/images/everyman123/post/8ab43033-32b9-4e36-9880-b0834475b51b/image.png)

---
완전 함수적 종속성(FFD: Full Functional Dependency)
애트리뷰트 B가 애트리뷰트 A에 함수적으로 종속하면서 애트리뷰트 A의 어떠한 진부분 집합에도 함수적으로 종속하지 않으면, 애트리뷰트 B가 애트리뷰트 A에 완전하게 함수적으로 종속한다고 말함.
이때 A는 복합 애트리뷰트
![](https://velog.velcdn.com/images/everyman123/post/69812e13-18aa-4641-a278-76f9a2119a10/image.png)

---

이행적함수적종속성 (transitive FD)
애트리뷰트 A,B,C가 있을 때, 애트리뷰트 C가 이행적으로 A에 종속한다 (A->C)는 것의 필요 충분 조건은
![](https://velog.velcdn.com/images/everyman123/post/06520de7-db2d-49ad-8457-01ce4df6e292/image.png)


## 릴레이션 분해

---
하나의 릴레이션을 두 개 이상의 릴레이션으로 나누는 것. 릴레이션 분해는 릴레이션에 존재하는 함수적 종속성에 관한 지식을 기반으로 함

릴레이션을 분해하면 중복이 감소하고, 갱신 이상이 줄어드는 장점이 있지만 몇 가지 문제들을 야기할 수 있음

- 분해되기 전에는 조인이 필요없는 질의가 분해 후에는 조인을 필요로 하는 질의로 바뀔 수 있음
- 분해된 릴레이션들을 사용하여 원래 릴레이션을 재구성하지 못할 수 있음

---
**무손실 분해**란 분해된 두 릴레이션을 조인하면 원래의 릴레이션에 있는 정보를 완전하게 얻을 수 있따는 것.

손실이란 릴레이션을 분해한 후에 조인을 통해 재구성 했을 때, 원래의 릴레이션ㄴ에 있는 정보보다 적거나 많은 것

## 제1 정규형,제2 정규형,제3 정규형,BCNF
---
제 1 정규형을 만족할 필요 충분 조건은 모든 애트리뷰트가 원자값만을 갖는다는 것, 즉 모든 애트리뷰트에 반복 그룹이 나타나지 않는 것
![](https://velog.velcdn.com/images/everyman123/post/1747e312-d1b6-41a5-9f3f-287fa89752ce/image.png)

---
제 2 정규형을 만족할 필요 충분 조건은 제 1 정규형을 만족하면서, 후보 키에 속하지 않는 애트리뷰트들이 기본 키에 완전하게 함수적으로 종속하는 것

기본 키가 두 개 이상의 애트리뷰트로 구성되었을 경우에만 제 1정규형이 제 2정규형을 만족하는가를 고려할 필요가 있음.
![](https://velog.velcdn.com/images/everyman123/post/6f941170-4cc1-407b-8bdc-d9f73157f48e/image.png)


--- 
제3 정규형을 만족할 필요 충분 조건은 제2 정규형을 맍고하면서, 키가 아닌 애트리뷰트가 기본 키에 이행적으로 종속하지 않는것
![](https://velog.velcdn.com/images/everyman123/post/1af7b628-3fbe-4794-940a-ca7abb8e1a83/image.png)


--- 
BCNF를 만족할 필요 충분 조건은 제3 정규형을 만족하고 모든 결정자가 후보 키이어야 한다.

제 3 정규형을 만족하는 대부분의 릴레이션들은 BCNF도 만족함.

- 키가 아니면서 결정자인 애트리뷰트와 그 결정자에 함수적으로 조속하는 애트리뷰트를 하나의 테이블에 넣음. 이 릴레이션에서 결정자는 기본 키가 된다
- 기존 릴레이션에 결정자를 남겨서 기본 키의 구성요소가 되도록 한다. 또한 이 결정자는 새로운 릴레이션에 대한 외래키 역할을 함
![](https://velog.velcdn.com/images/everyman123/post/a1f63115-821b-4709-8c4a-8cded0413159/image.png)

---
![](https://velog.velcdn.com/images/everyman123/post/d57e3229-ee6e-49e6-8f40-4be911d852fb/image.png)


## 역정규화

- 정규화 장점
  - 정규화 단계가 진행될수록 중복이 감소하고 갱신 이상도 감소
  - 무결성 제약조건을 시행하기 위해 필요한 코드의 양도 감소
- 단점
  - 정규화가 진행될수록 릴레이션이 계속 나뉘어진다
  - 조인의 필요성이 증가


--- 
많은 데이터베이스 응용에서 검색 질의의 비율이 갱신 질의의 비율보다 훨씬 높음. 역정규화는 주어진 응용에서 빈번하게 수행되는 검색 질의들의 수행 속도를 높이기 위해서 이미 분해된 두 개 이상의 릴레이션들을 합쳐서 하나의 릴레이션으로 만드는 작업, 즉, 역정규화는 보다 낮은 정규형으로 되돌아가는 것
![](https://velog.velcdn.com/images/everyman123/post/96701ed5-776d-4fac-9c87-4f0050de0581/image.png)


# 뷰
---
ANSI/SPARC 3단계 아키텍처에서 외부 뷰는 사용자가 보는 데이터베이스의 구조. **관계 데이터베이스에서의 뷰는 외부 뷰가 아닌, 하나의 가상 릴레이션을 의미**

**뷰는 기존의 기본 릴레이션(실제 릴레이션)에 대한 SELECT 문의 형태로 정의 됨. **뷰는 릴레이션으로부터 데이터를 검색하거나 갱신할 수 있는 동적인 창의 역할
![](https://velog.velcdn.com/images/everyman123/post/212f78b5-7c5b-4cc6-947f-ddf1c15b0bac/image.png)

---
**스냅샵(snapshot)은 어느 시점에 SELECT문의 결과를  기본 릴레이션의 형태로 저장해 놓은 것.** 어떤 시점의 조직체의 현황, 예를 들어 몇년 몇월 시점에 근무하던 사원들의 정보 등이 스냅샷으로 정의될 수 있음

```
CREATE VIEW 뷰이름 [(애트리뷰트(들))] 
AS SELECT문 
[WITH CHECK OPTION];

CREATE VIEW 	EMP_DNO3 (ENO,ENAME,TITLE) 
AS SELECT 	EMPNO, EMPNAME, TITLE 
FROM 		EMPLOYEE 
WHERE 		DNO=3;

CREATE VIEW 	EMP_PLANNING 
AS SELECT 	E.EMPNAME, E.TITLE, E.SALARY 
FROM 		EMPLOYEE E, DEPARTMENT D 
WHERE 		E.DNO=D.DEPTNO 
	AND	D.DEPTNAME='기획';
```
![](https://velog.velcdn.com/images/everyman123/post/d19b8439-d2f3-4cbe-a279-696912f1b87a/image.png)

뷰의 이름 다음에 애트리뷰들을 생략하면 뷰를 정의하는데 사용된 SELECT문의 SELECT절에 열겨된 애트리뷰트들의 이름이 뷰에 포함됨

산술식 또는 집단함수를 사용할 경우, 조인할 때 가져온 애트리뷰트들의 이름이 같게 되는 경우에는, 모든 애트리뷰트들의 이름을 지정해야 함

---
뷰를 사용하여 데이터를 접근할 때 관계 DBMS에서 거치는 과정은 다음과 같다

-  시스템 카탈로그로부터 뷰의 정의, 즉 SELECt문을 검색
- 기본 릴레이션에 대한 뷰의 접근 권한을 검사
- 뷰에 대한 질의를 기본 릴레이션에 대한 동등한 질의로 변환
![](https://velog.velcdn.com/images/everyman123/post/444499d8-a8aa-4537-b38f-3f2eaa1fec7c/image.png)

---
뷰의 장점
- 뷰는 복잡한 질의를 간단하게 표현할 수 있게 함
![](https://velog.velcdn.com/images/everyman123/post/f42710c3-9ed1-4ebc-9cba-31d8175ffb3e/image.png)
- 뷰를 정의할 때 WITH CHECK OPTION을 사용하면, 뷰는 데이터 무결성을 보장하는데 활용됨
- 기본적으로 뷰를 통해 투플을 추가하거나 수정할 대, 투플이 뷰를 정의하는 SELECT문의 WHERE절의 기준에 맞지 않으면 뷰의 내용에서 삭제된다
- 뷰는 데이터의 독립성을 제공한다. 뷰는 데이터베이스의 구조가 바뀌어도 기존의 질의를 다시 작성할 필요성을 줄일 수 있음
- 뷰는 데이터 보안 기능을 제공함. 뷰는 원본이 되는 기본 릴레이션에 직접 접근할 수 있는 권한을 부여하지않고, 뷰를 통해 데이터를 접근하도록 한다
- 뷰는 일반적으로 기본 릴레이션의 일부 애트리뷰트들 또는  일부 투플들을 검색하는 SELECT문으로 정의되므로, 뷰를 통해서 접근하면 기본 릴레이션의 일부만 검색할 수 있음
- 동일한 데이터에 대한 여러가지 뷰를 제공함. 뷰는 사용자들의 그룹이 각자 특정한 기준에 따라 데이터를 접근하도록 한다.


---
뷰에 대한 갱신도 기본 릴레이션에 대한 갱신으로 변환됨

갱신이 불가능한 뷰는 다음과 같다
- **릴레이션 위엥서 정의되었으나, 그 릴레이션의 기본 키가 포함되지 않는 뷰**
- 기본 릴레이션의 애트리뷰트들 중에서 뷰에 포함되지 않은 애트리뷰트에 대해 NOT NULL이 지정되어 있을 때 (뷰로 무언가를 넣을때 이거에 대한 정보가 없으므로 터진다)
- 집단 함수가 포함된 뷰
- 조인으로 정의된 뷰 (너무 복잡해져)
![](https://velog.velcdn.com/images/everyman123/post/67eb3f87-3e81-4e5d-b625-bd5f56ed13a4/image.png)

---
## 관계 DBMS의 시스템 카탈로그
시스템 카탈로그는 데이터베이스의 객체와 구조들에 관한 모든 데이터를 포함

시스템 카탈로그를 메타데이터라고 함. 메타데이터는 데이터에 관한 데이터라는 의미. **시스템 카탈로그는 데이터 사전 또는  시스템 테이블이라고도 부름**

시스템 카탈로그는 사용자 및 질의 최적화 모듈 등 DBMS 자신의 구성요소에 의해서 사용됨. 시스템 카탈로그는 표준화되어 있지 않아서, 관계 DBMS마다 서로 다른 형태로 시스템 카탈로그 기능을 제공

---
- 카탈로그 활용
![](https://velog.velcdn.com/images/everyman123/post/49cf92eb-7dfc-47f0-98f7-55a3fdbc6f8c/image.png)

- SELECT문이 문법적으로 정확한지 검사
- SELECT문에서 참조하는 EMPLOYEE릴레이션이 데이터베이스에 존재하는지 감시
- EMPLOYEE릴레이션에 SELECT절의 애트리뷰트와 WHERE절에서 사용된 애트리뷰트가 존재하는지 확인
- SALARY 애트리뷰트의 데이터 타입이 숫자형인지 검사. TITLE이 문자와 비교되었으므로 TITLE의 데이터 타입 검사
- TITLE 애트리뷰트와 DNO 애트리뷰트에 인덱스가 정의되어 있는지 확인
- 둘다 인덱스가 존재한다면 DBMS가 두 인덱스 중에서 조건을 만족하는 투플 수가 가장 적은 것을 선택하기 위해 시스템 카탈로그를 사용 (전체 투플 수와 각 인덱스의 존재하는 상이한 값들의 개수를 유지)
---
질의 최적화는 DBMS가 질의를 수행하는 여러 방법들 중에서 가장 비용이 적게 드는 방법을 찾는 과정. 질의 최적화 모듈이 정확한 결정을 내릴 수 있도록, DBMS는 시스템 카탈로그에 다양한 정보를 유지함

--
관계 DBMS의 시스템 카탈로그는 사용자 릴레이션과 같은 형태로 저장되기에, 회복 기법과 동시성 제어 기법을 동일하게 사용할 수 잇음. 시스템 카탈로그는 SELECT문을 사용하여 내용을 검색할 수 있음.

시스템 카탈로그에는 릴레이션, 애트리뷰트, 인덱스, 사용자, 권한 등 각 유형마다 별도의 릴레이션이 유지됨.
![](https://velog.velcdn.com/images/everyman123/post/ebfcd430-3a39-422c-9d2f-2f892167a0b7/image.png)
**어떤 사용자도 시스템 카탈로그를 직접 갱신할 수 없음. 즉, DELETE, UPDATE 또는 INSERT문을 사용하여 시스템 카탈로그를 변경할 수 없음.**

--- 
시스템 카탈로그에 유지되는 통계 정보

- 릴레이션마다 투플의 크기, 투플 수, 각 블록의 채우기 비율, 블록킹 인수, 릴레이션의 크기(블록 수)
- 뷰마다 뷰의 이름과 정의
- 애트리뷰트마다 애트리뷰트의 데이터 타입과 크기, 애트리뷰트 내의 상이한 값들의 수, 애트리뷰트 값의 범위, 선택율(조건을 만족하는 투플 수/전체 투플 수)
- 사용자마다 접근할 수 있는 릴레이션과 권한
- 인덱스마다 인덱스된 애트리뷰트, 비/클러스터링 인덱스 여부, 밀집/희소 인덱스 여부, 인덱스의 높이, 1단계인 덱스의 블록 수

---
## 오라클의 시스템 카탈로그
시스템 카탈로그를 데이터 사전(data dictionary)이라고 부름. 데이터 사전은 시스템 테이블 스페이스에 저장됨. 이는 기본 테이블과 데이터 사전 뷰로 구성됨.

사용자는 기본 테이블의 정보가 암호화된 형태로 저장되어 있기 때문에 직접 접근할 필요가 없으며, 일반적으로 이해하기 쉬운 형식의 정보를 제공하는 데이터 사전 뷰를 접근.

데이터 사전 뷰의 세 부류
![](https://velog.velcdn.com/images/everyman123/post/3986e9da-b2c3-4381-9ace-4802421c486b/image.png)

---
통계 정보는 ANALYZE문을 사용하여 갱신할 수 있음.
테이블에 대한 통계 정보는 ANALYZE TABLE 명령을 사용해서 갱신하고, 인덱스에 대한 통계 정보는 ANALYZE INDEX 명령을 사용해서 갱신.

ANALYZE 명령의문법

```
ANALYZE 객체_유형 객체_이름 연산 STATISTICS
- 객체 유형은 테이블,인덱스 등을 나타냄
- 객체 이름은 객체의 이름
- 연산에 COMPUTE가 사용되면 전체 테이블을 접근하여 통계 정보를 계산
- 연산에 ESTIMATE가 사용되면 데이터 표본을 추출하여 통게 정보를 계산
```
주기적으로 ANALYZES 작업을 수행해야 한다. 다량의 데이터를 일괄 작업으로 처리한 경우 등에는 바로 ANALYZE 작업을 수행하는 것이 필요


# 트랜잭션
---
**트랜잭션**: 많은 사용자들이 동시에 데이터베이스의 서로 다른 부분 또는 동일한 부분을 접근하면서 데이터베이스를 사용함

- 동시성 제어 
    - **동시에 수행되는 트랜잭션들이 데이터베이스에 미치는 영향을, 순차적으로 수행하였을 때 데이터베이스에 미치는 영향과 같도록 함**
    - 많은 사용자가 데이터베이스를 동시에 접근하도록 하면서 데이터베이스의 일관성을 유지함
    ![](https://velog.velcdn.com/images/everyman123/post/ede757b7-12c5-40d6-86a1-cc5bc0fb25a5/image.png)


위의 두 개의 UPDATE문은 둘 다 완전하게 수행되거나 한 UPDATE문도 수행되어서는 안되도록, **즉 하나의 트랜잭션처럼 DBMS가 보장해야함**


- 회복
  - 데이터베이스를 갱신하는 도중에 시스템이 고장나도 데이터베이스의 일관성을 유지함
  ![](https://velog.velcdn.com/images/everyman123/post/20ad1078-a00f-4634-9ba0-251781de0529/image.png)
  - LOG 유지

---
## 트랜잭션 개요

ACID 특성

(1) 원자성: 트랜잭션의 모든 연산들이 완전히 수행되거나 전혀 수행되지 않음
(2) 일관성: 수행 전후 모두 일관된 상태여야 한다
(3) 고립성: 트랜잭션이 데이터를 갱신하는 동안 다른 트랜잭션들이 데이터에 대해 접근하지 못하도록 차단한다.
(4) 지속성: 트랜잭션이 완료되면 이 트랜잭션이 갱신한 것은 시스템이 고장나더라도 손실되지 않는다.
![](https://velog.velcdn.com/images/everyman123/post/0b970e0a-0129-4b38-9b9d-979a33ff92b3/image.png)

![](https://velog.velcdn.com/images/everyman123/post/0f92a2fc-11e5-4e4c-8dc1-47f870b018f6/image.png)

---
## 동시성 제어
- 동시성 제어 
    - **동시에 수행되는 트랜잭션들이 데이터베이스에 미치는 영향을, 순차적으로 수행하였을 때 데이터베이스에 미치는 영향과 같도록 함**
- 동시성 제어 기법
  - 다수의 트랜잭션들을 동시에 수행하는 환경에서 부정확한 결과를 생성할 수 있는, 트랜잭션들 간의 간섭이 생기지 않도록 한다.


- 직렬 스케쥴
  - 여러 트랜잭션들의 집합을 한 번에 한 트랜잭션씩 차례대로 수행함
- 비직렬 스케쥴
  - 여러 트랜잭션들을 동시에 수행함
- 직렬가능
  - 비직렬 스케줄의 결과가 어떤 직렬 스케줄의 수행 결과와 동등함
  

- 데이터베이스 연산
  - Input(x): 데이터베이스 항목 x를 포함하고 있는 블록을 주기억 장치의 버퍼로 읽는다.
  - Output(x): 데이터베이스 항목 x를 포함하고 있는 블록을 디스크에 기록한다.
  - read_item(x): 주기억 장치 버퍼에서 데이터베이스 항목 x의 값을 프로그램 변수 x로 복사한다.
  - write_item(x): 프로그램 변수 x의 값을 주기억 장치 내의 데이터베이스 항목 x에 기록한다.
  ![](https://velog.velcdn.com/images/everyman123/post/2065632f-8014-488d-9982-63e41471d86d/image.png)


- 동시성 제어를 하지 않고 다수의 트랜잭션을 수행할 때 생길 수 있는 문제
  - 갱신 손실: 수행 중인 트랜잭션이 갱신한 내용을 다른 트랜잭션이 덮어 씀
  ![](https://velog.velcdn.com/images/everyman123/post/41c9ff66-5c70-42d0-832b-ea2e714d29e1/image.png)

  - 오손 데이터 읽기: 완료되지 않은 트랜잭션이 갱신한 데이터를 읽는 것
  ![](https://velog.velcdn.com/images/everyman123/post/88a895b5-8097-4916-80a1-886188e09d0e/image.png)

  - 반복할수 없는 읽기: 한 트랜잭션이 동일한 데이터를 두 번 읽을 때 서로 다른 값을 얻는 것
  ![](https://velog.velcdn.com/images/everyman123/post/fe25b41a-9b25-474f-bfd5-012f54f8ac86/image.png)

---
# 로킹
- 데이터  항목을 로킹하는 개념은 동시에 수행되는 트랜잭션들의 동시성을 제어하기 위해서 사용되는 기법
- 로크는 데이터베이스 내의 각데이터 항목과 연관된 하나의 변수
- 트랜잭션이 수행을 시작하여 데이터 항목을 접근할 때마다 요청한 로크에 관한 정보는 로크 테이블등에 유지됨
- 트랜잭션에서 데이터 항목을 접근할 때 로크를 요청하고, 접근을 끝낸 후에 로크를 해제함

- 갱신 목적 접근: 독점 로크 (X-lock,exclusive lock)을 요청함
- 판독(일기)목적 저근: 공유 로그(S-lock,shared lock)를 요청함
![](https://velog.velcdn.com/images/everyman123/post/d10760c4-b725-48d1-8973-dc5244fa5fde/image.png)
---
- 2단계 로킹 프로토콜 (2-phase locking protocol)
  - 로크를 요청하는 것과 해제하는 2단계
  - 로크 확장 단계가 지나면 수축 단계에 들어감
  - 일단 로크를 한 개라도 해체하면 로크 수축 단계
  
**로크 확장 단계(1단계)**에서는 트랜잭션이 데이터 항목에 대하여 새로운 로크를 요청할 수 있지만, 보유하고 있던 로크를 하나라도 해체할 수 없음

**로크 수축 단계(2단계)**에서는 보유하고 있던 로크를 해체할 수 있지만, 새로운 로크를 요청할 수 없음 로크를 조금씩 해체할 수도 있고, 트랜잭션이 완료 시점에 이르렀을 때 한꺼번에 모든 로크를 해체할 수 도 있음. 일반적으로 하번에 해체

**로크 포이트**는 한 트랜잭션에서 필요로 하는 모든 로크를 걸어놓은 시점
![](https://velog.velcdn.com/images/everyman123/post/b4c239a2-3505-434e-8857-2e836faaa4a1/image.png)


---
2단계 로킹 프로토콜에서 **데드록이 발생할 수 있음**
![](https://velog.velcdn.com/images/everyman123/post/2db0577d-937a-418c-afd2-b1e166890e54/image.png)

서로가 서로의 로크를 기다리는 상태
데드록을 해결하기 위해서는 데드록을 방지하는 기법이나, 데드록을 탐지하고 희생자를 선정하여 데드록을 푸는 기법 등을 사용함.(최근 거를 희생)

---

트랜잭션이 접근하는 투플의 수에 따라 로크를 하는 데이터 항목의 단위를 구분하는 것이 필요함. 한 트랜잭션에서 로크할 수 있는 데이터 항목이 두 가지 이상 있으면 다중 로크 단위(multiple granularity)라고 말함.

데이터베이스에서 로크 할 수 있는 단위로는 데이터베이스, 릴레이션, 디스크 블록, 투플 등.

일반적으로 DBMS는 트랜잭션에서 접근하는 투플 수에 따라 자동적으로 로크 단위를 조정함. 로크 단위가 작을수록 로킹에 따른 오버헤드 및 동시성의 정도가 증가함.

  ![](https://velog.velcdn.com/images/everyman123/post/7e1b40bd-ed7e-4970-be1f-cb83be83cd88/image.png)

---
* 팬텀 문제란 한 트랜잭션에 속한 첫 번째 select문과 두 번째 select의 수행 결과가 다르게 나타나는 것

![](https://velog.velcdn.com/images/everyman123/post/8cb63f61-9e50-4647-b5e1-3186f612a579/image.png)




---
## 회복

트랜잭션을 수행하는 도중에 시스템이 다운되었을 때, 수행 효과가 디스크의 데이터베이스에 일부 반영되었을 수 있음. 원자성을 보장하기 위해서 이 트랜잭션이 **데이터베이스에 반영했을 가능성이 있는 갱신 사항을 취소(UNDO)해야 함.**
-> 도중에 뒤지면 UNDO

트랜잭션이 완료된 직후에 시스템이 다운되면, 모든 갱신 효과가 주기억 장치로부터 디스크에 기록되지 않았을 수 있음. **회복 모듈은 이 트랜잭션의 갱신 사항을 재수행(REDO)하여 트랜잭션의 갱신이 지속성을 갖도록 해야 함.**
-> 끝나고 뒤지면 REDO

---
- 트랜잭션의 원자성과 지속성을 보잗하기 위해 DBMS는 **log**라고 불리는 특별한 파일을 유지

- 데이터베이스의 항목에 영향을미치는 모든 트랜잭션의 연산들에 대해서 로그 레코드를 기록함. 각 로크 레코드는 로그 순서 번호(LSN)로 식별됨
![](https://velog.velcdn.com/images/everyman123/post/d3a1e008-0f3b-4e08-ad8a-c93d36723689/image.png)

- 주기억 장치내의 로그 버퍼에 로그 레코드들을 기록하고 로그 버퍼가 꽉 찰 때 디스크에 기록
- 로그는 데이터베이스 회복에 필수적이므로 일반적으로 안전 저장 장치에 저장됨.로그를 두개의 디디스크에 중복해서 저장하는 이중로그
- 각 로그 레코드가 어떤 트랜잭션에 속한 것인가를 식별하기 위해서 각 로그 레코드마다 트랜잭션 ID를 포함시킴. 동일한 트랜잭션에 속하는 로그 레코드들은 연결 리스트로 유지됨
---
![](https://velog.velcdn.com/images/everyman123/post/24e097a4-750e-401b-8314-0330e0760c6d/image.png)

![](https://velog.velcdn.com/images/everyman123/post/5438bc7e-3e9d-47a4-8ff1-c7b94b3a45da/image.png)

- 트랜잭션의 갱신 연산이 모두 끝나고, 갱신 사항이 로그에 기록되었을 때를 트랜잭션의 완료점(commit point)라고 함.
- 로그먼저쓰기(WAL: Write-Ahead Logging)
  - 트랜잭션이 데이터베이스를 갱신하면 주기억 장치의 데이터베이스 버퍼에 갱신 사항을 기록하고, 로그 버퍼에는 이에 대응되는 로그 레코드를 기록함
  - 데이터베이스 버퍼가 먼저 기록되고 시스템이 다운되면,로그 레코드가 없어서 이전값을 알수 없으므로 트랜잭션의 취소가 불가능. 따라서 데이터베이스 버퍼보다 로그 버퍼를 먼저 디스크에 기록해야 함.
  
- 체크포인트
  - 시스템이 다운된 시점으로부터 오래 전에 완료된 트랜잭션들은 이미 디스크에 반영되었을 가능성이 큼.
  - 로그를 사용하더라도 어떤 트랜잭션의 갱신 사항이 주기억 장치 버퍼로부터 디스크에 기록되었는가를 구분할 수 없음.
  - 따라서 DBMS는 회복시 재수행할 트랜잭션의 수를 줄이기 위해서 주기적으로 체크포인트를 수행함.  체크포인트 시점에는 주기억 장치의 버퍼 내용이 디스크에 강제로 기록되므로, 디스크상에서 로그와 데이터베이스의 내용이 일치하게 됨.
  
  ![](https://velog.velcdn.com/images/everyman123/post/3c002bb9-21ae-4a9b-bc2d-543019ca2650/image.png)


---
## PL/SQL의 트랜잭션
오라클에서 한 트랜잭션은 암시적으로 또는 명시적으로 끝날 수 있음.

트랜잭션은 SQL문이 실행될 때 시작되어 데이터 정의어/데이터 제어어를 만나거나, Oracle SQL Developer를 정상 종료했을 때 암시적으로 완료(commit)됨.

COMMIT, ROLLBACK, SAVEPOINT문을 사용하여 트랜잭션의 논리를 명시적으로 제어할 수 있음.

- COMMIT: 트랜잭션에서 수행한 데이터 조작어의 결과를 데이터베이스에 모두 반영하고 트랜잭션을 완료
- ROLLBACK: 트랜잭션에서 수행한 데이터 조작어의 결과를 데이터베이스에서 모두 되돌리고 트랜잭션을 철회
- SAVEPOINT: 트랜잭션 내에 저장점을 표시하여 트랜잭션을 더 작은 부분으로 나눔
- ROLLBACK TO SAVEPOINT: 트랜잭션에서 지정된 저장점 이후에 갱신된 내용만 되돌림
![](https://velog.velcdn.com/images/everyman123/post/08502cb2-4357-4c6e-a0f5-9cf559ae3617/image.png)

---
만일 트랜잭션이 데이터베이스를 읽기만 한다면 트랜잭션이 읽기 전용임을 명시하여 DBMS가 동시서의 정도를 높일 수 있음.
```SET TRANSACTION READ ONLY;
SELECT AVG(SALARY) 
FROM EMPLOYEE 
WHERE DEPT='개발부';

// 읽기 전용에서는 갱신 작업이 불가능
SET TRANSACTION READ ONLY;
UPDATE EMPLOYEE 
SET SALARY = SALARY * 1.06; 

// 읽기, 갱신 가능
SET TRANSACTION READ WRITE;
UPDATE EMPLOYEE 
SET SALARY = SALARY * 1.06; 

```

---
**고립 수준**
SQL2에서 사용자가 동시성의 정도를 몇 가지로 구분하여 명시할 수 있음. 고립 수준은 한 트랜잭션이 다른 트랜잭션과 고립되어야 하는 정도를 나타냄.

고립 수준이 낮으면 동시성은 높아지지만 데이터의 정확성은 떨어짐. 고립 수준이 높으면 데이터가 정확해지지만 동시성이 저하됨.

응용에서 명시한 고립 수준에 따라 DBMS가 사용하는 로킹 동작이 달라짐. 한 트랜잭션에 대해 명시한 고립 수준은 다른 트랜잭션의 고립 수준에 영향을 미치지 않음.

(1) READ UNCOMMITTED
- 가장 낮은 수준의 고립
- 트랜잭션 내의 질의들이 공유 로크를 걸지 않고 데이터를 읽음
- 오손 데이터를 읽을 수 있음
- 갱신하려는 데이터에 대해서는 독점 로크를 걸고, 트랜잭션이 끝날 때까지 보유함

(2) READ COMMITTED
- 읽으려는 데이터에 대해서 공유 로크를 걸고, 읽기가 끝나자마자 로크를 해제함
- 동일한 데이터를 읽으면, 이전에 읽은 값과 다른 값을 읽는 경우가 생길 수 있음
- 갱신하려는 데이터에 대해서는 독점 로크를 걸고, 트랜잭션이 끝날 때까지 보유함
- PL/SQL DEFAULT

(3) REPEATABLE READ
- 검색되는 데이터에 대해 공유 로크를 걸고, 트랜잭션이 끝날때까지 보유
- 트랜잭션 내에서 동일한 질의를 두 번 이상 수행할때, 이전에 읽은 값이 항상 동일하게 유지됨
- 갱신하려는 데이터에 대해서는 독점 로크를 걸고, 트랜잭션이 끝날때까지 보유함

(4) SERIALIZABLE
- 가장 높은 고립 수준
- 검색되는 투플들 뿐만 아니라, 인덱스에 대해서도 공유 로크를 걸고 트랜잭션이 끝날때까지 보유함
- 한 트랜잭션 내에서 동일한 질의를 두번 이상 수행할때, 매번 같은 값을 포함한 결과가 나옴
- 갱신하려는 데이터에 대해서는 독점 로크를 걸고, 트랜잭션이 끝날때까지 보유
- SQL2의 디폴트 고립 수준
---
- REPEATABLE READ vs SERIALIZABLE
SELECT col1 FROM A WHERE col1 BETWEEN 1 AND 10;

  - REPEATABLE READ
    - 이 범위에 해당하는 데이터가 col1=1과 5인 경우, 다른 사용자가 col1이 1이나 5인 Row에 대한 UPDATE가 불가능
    - col1이 1과 5를 제외한 나머지 범위에 해당하는 Row를 INSERT하는 것은 가능
  - SERIABLIZABLE
    - 범위에 해당되는 데이터에 대한 수정 및 입력이 불가능
    - SQL의 결과가 항상 동일함
    
  
 SET TRANSACTION READ WRITE
ISOLATION LEVEL SERIALIZABLE;

SET TRANSACTION READ WRITE
ISOLATION LEVEL REPEATABLE READ;

SET TRANSACTION READ WRITE
ISOLATION LEVEL READ COMMITTED;

SET TRANSACTION READ WRITE
ISOLATION LEVEL READ UNCOMMITTED;
  


![](https://velog.velcdn.com/images/everyman123/post/3a103de5-acbb-49ff-97ae-63c1f11e6b93/image.png)




