# 설계 원리

- 어떻게 실현할 것인가를 구체적으로 결정하는 활동
- 시스템의 논리 구성을 결정
- 설계 단계의 중심은 요구를 실현하는 솔루션
- 아키텍처 - 소프트웨어 설계에서 특히 중요하며 스프트웨어의 기본 구조를 나타냄. 시스템 성능, 보안, 가용성 등의 품질이 아키텍처를 어떻게 구성하였느냐에 달려있음
- 설계작업
  - 기본 구조 설계 - 아키텍처 설계로 각 모듈의 역할과 인터페이스를 정의
  - 상세 설계 - 모듈 내부의 알고리즘, 데이터를 명세화

## 설계 기본 개념

- 설계는 프로그램이라는 구체적인 대상을 다루지만, 개념적인 작업 -> 설계 작업에 기초가 되는 개념을 정확히 이해하고 적용할 수 있어야 함
- 전통적인 설계 방법인 분할 정복, 추상화, 합성 등의 원리를 적용하여 대규모 문제를 다루었지만 최근에는 아키텍처 기반의 설계 방법으로 바뀜 -> 아키텍처를 고려한 설계가 되어야 복잡한 문제를 다룰 수 있고 변경에 잘 대처할 수 있기 때문

### 서브시스템, 모듈

- 아키텍처 - 시스템을 구성하는 컴포넌트와 컴포넌트 상호작용의 집합
- 컴포넌트 - 독립적으로 취급될 수 있는 단위로 서브시스템 또는 모듈이라고 부름. 대부분의 컴포넌트들은 재사용 가능하도록 설계됨. 반면 특정한 목적, 예를 들면 특정 시스템의 사용자 인터페이스를 제공하는 기능 등을 수행하는 경우도 있음. 프레임워크는 컴포넌트의 한 종류
- 모듈 - 프로그래밍 언어의 문법 구조에서 정의된 컴포넌트. Ex) 메소드, 클래스, 패키지는 Java 프로그램의 모듈임. C언어에서의 모듈은 파일과 함수
- 서브시스템 - 클래스의 모임, 즉 패키지이며 다른 서브시스템과 상호작용하기 위하여 정의된 인터페이스를 가짐. 시스템은 정의 가능한 책임과 목적들을 가지고 있고 소프트웨어나 하드웨어로 구성된 논리적 개체
- 설계는 각 서브시스템이 제공하는 서비스의 명세와 작동되는 제약 조건을 제공

### 설계 관점

1. 모듈 관점 - 일정한 책임을 구현한 코드 단위인 모듈과 그 관계로 소프트웨어 구조를 설명하는 관점 / 분할, 사용관계, 계층 구조, 데이터 모델
2. 컴포넌트 관점 - 실행될 때 동작하는 요소와 상호작용으로 구조를 설명하는 관점 / 클라이언트-서버, 파이프필터, 출판 구독, 이벤트 중심, 리파지토리
3. 할당 관점 - 소프트웨어의 하드웨어 설치, 작업 할당, 구현, 데이터 저장 등에 대한 관점 - 배치 / 설계 / 작업 할당 / 구현 / 데이터 저장

### 설계 작업 과정

1. 설계 목표 설정 - 전체 시스템에 대한설계 목표를 파악하고 결정. 예를 들어 전화 교환 시스템을 개발한다면 고장에 대한 내성, 안전과 보안, 최대 성능이 설계 목표가  될 수 있음
2. 스타일 결정 - 시스템이나 서브시스템의 타입을 결정하기 위하여 설계 목표와 유형에 맞은 아키텍처 스타일을 선택. 적용할 수 있는 아키텍처 스타일이 있다면 이를 적용하여 시스템의 표준 아키텍처를 설계. 없다면 맞춤형 아키텍처를 설계
3. 서브시스템의 기능, 인터페이스 명세 - 서브시스템 사이의 인터페이스를 정의하고 서브시스템 사이의 상호작용을 위한 동작을 작성
4. 아키텍처 설계 검토 - 설계한 아키텍처가 요구, 설계 목표, 설계 원리를 잘 만족하는지 검토

## 품질 목표

- 비기능 요구 사항 - 품질 특성이며 시스템 설계안을 결정하는 요소들
- 아키텍처는 설계에 대한 여러 관점을 명시적으로 언급하여야 함
- 개발자는 기능적인 요구를 이해하고 동시에 기능들이 비기능적인 요구, 즉 품질 목표를 만족하도록 플랫폼을 만들어야 함
- 품질 요구 사항을 충족시키도록 설계할 때 다른 속성에 미치는 영향을 고려하여 설계하여야 함
- 설계작업은 품질 속성의 우선순위를 정하고 절충하는 일이 중요

## 전통적인 설계 원리

- 효율성과 단순성을 중요하게 생각

### 추상화

- 컴포넌트 구현에 대한 자세한 사항을 염려하지 않고 추상적인 수준으로 컴포넌트를 다루는 도구
- 컴포넌트나 시스템은 외부에 서비스를 제공
- 컴포넌트의 추상 - 컴포넌트가 어떻게 동작하는지 내부의 상세한 사항에 구애받지 않고 외부에 보이는 동작을 나타내는 것
- 추상화 - 대상에 대하여 특정한 목적에 관련된 정보에 집중하고 나머지 정보는 무시하는 관점
- 소프트웨어를 데이터나 절차적인 동작 관점으로 정의할 수 있음 Ex) 클라이언트와 서버의 정보교환을 주고받는 메시지 데이터의 구조적인 정보만으로 추상화할 수 있음
- 복잡성을 줄이고 복잡한 소프트웨어 시스템을 효율적으로 다루고 구현할 수 있게 함
- 설계 작업 과정에 필수적인 요소이며 문제 분할의 근본이 됨