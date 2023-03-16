# Operating_System
컴퓨터공학과 운영체제 정리입니다.

## 1.1 운영체제란?

```
운영체제란 Operating System(OS) 컴퓨터를 운영하기 위한 수법과 절차를 모은 소프트웨어 체계입니다.
운영체제의 가장 기본적인 역할 중의 하나는 사용자로 하여금 하드웨어인 입.출력 장치를 편리하게 사용할 수 있게 하는 것이다.
만약 운영체제가 없다면 일반 사용자는 키보드, 마우스, 모니터, 프린터 등을 사용할 수 없어서 컴퓨터는 무용지물이 된다.

운영체제는 시스템 콜이라고 부르는 서비스 요청 접속 창구를 라이브러리 형태로 제공한다.
사용자는 시스템 콜 라이브러리를 호출하는 프로그램을 작성하여 실행함으로써 운영체제가 제공하는 서비스를 받을 수 있다.
자주 사용되는 운영체제 서비스는 미리 작성되어 시스템에 탑재되어 있는 프로그램을 실행시켜 호출할 수 있는데 이러한 프로그램을 시스템 명령어라 부른다.
```

## 1.2 운영체제의 유형(발전과정)

### 1. 단일 프로그래밍 일괄 처리 시스템(Single-stream Batch(일괄로 묶다) Processing)
```
단일 프로그래밍 일괄 처리 시스템 환경에서 사용자는 컴퓨터에 접근할 수 없었으므로 프로그램을 천공 카드에
작성하여 관리자에게 제출하였고, 운영체제는 오직 하나의 프로그램만을 적재하여 차례차례 실행시켰다.

적재된 프로그램이 오직 하나 밖에 없었으므로, 사용자 프로그램이 입출력을 요구했을 때 운영체제는 입출력이
완료될 때까지 프로세서를 기다려야 했으므로 허비하는 시간(Idle Time)이 많았다.
```

### 2. 다중 프로그래밍 일괄 처리 시스템(Multiprogramming Batch Programming)
```
다중 프로그래밍 일괄 처리 시스템에서는 사용자 프로그램을 동시에 여러 개 적재시켜 실행중인 프로그램이
입출력을 요구하면 그 입출력 작업이 진행되는 동안에 다른 프로그램을 실행시켜줌으로써 프로세서의 유후 시간을 줄였다.

그러나 적재된 프로그램들의 완료 시간이 다른 프로그램의 입출력 요구 빈도에 따라 큰 영향을 받으므로 각 프로그램들의 완료시간
편차가 심하다.
```

### 3. 시분할 시스템(Time-Sharing System)
```
시분할 시스템은 여러 개의 프로그램을 짧은 시간(타임 퀀텀) 동안 조금씩 번갈아 가면서 처리함으로써 사용자에게
시스템을 독차지하고 있다는 느낌을 준다.

시분할 시스템은 다수의 사용자들이 단말기를 통해서 컴퓨터에 동시 접속하는 대화적 처리 환경에 적합하다.
```

### 4. 병렬 처리 시스템(Parallel Processing Systems)
```
병렬 처리 시스템은 여러 개의 처리기(CPU)를 이용하여 여러 개의 프로그램들을 병렬로 처리한다.
병럴 처리 시스템의 목적은 성능 향상과 신뢰성 향상(결함 허용)에 있다.
병렬 처리(Parallel Processing)은 어느 시점을 기준으로 보았을 때 2개 이상의 프로그램을 처리하는 것을 말하고,
병행 처리(Concurrent Processing)는 어느 시점을 기준으로 보았을 때는 오직 하나의 프로그램만을 처리하지만,
이들을 번갈아 처리함으로써 일정 기간 동안 결국 여러 개의 프로그램을 처리하는 것을 말한다.

병렬 처리를 위한 다중 처리기 시스템은 분산 처리 시스템의 일종으로 강결합(Tightly-coupled System)이라 부르기도 한다.
다중 처리기 시스템은 처리기들 사이의 버스 연결 방식에 따라 단일 공유 버스, 다중 버스, 크로스바 스위치 버스, 계층적 버스
다중 포트 메모리 버스 등으로 분류된다.

처리기들이 독립적이지 않고 주어진 기계 명령어에 대하여 서로 긴밀하게 협조하여 서로 다른 데이터에 대한 동일한 연산 처리를
수행하는 다중 처리기 형태가 있는데 배열(혹은 벡터) 처리기가 그 대표적인 예이다.
```

### 병렬 처리 시스템의 종류
```
병렬 처리 시스템은 대칭형과 비대칭형으로 나뉘는데 대칭형은 CPU가 모두 운영체제를 이용하게 될 때(경쟁 상황일 때)
역할의 범위가 동등하여 운영체제의 부담이 커지게 된다. 

이러한 운영체제의 부담을 줄이기 위해서 비대칭 시스템이 있는데 비대칭 시스템은 마스터-슬레이브 관계가 되어
마스터인 경우에만 운영체제를 사용할 수 있게 되어 운영체제의 구현이 간단해지는 장점이 있다.
하지만 마스터가 고장나면 대책이 없다.
```

### 4. 분산 처리 시스템의 일종인 강결합 시스템(시스템 버스, 메모리 등이용)
```
1. 단일 공유 버스 : CPU들이(처리기들)이 하나의 버스를 공유하여 메모리에 접근하므로 경쟁 구도, 배타적인 성향을 띠며
CPU를 추가해도 성능은 갈 수록 저하된다. 어느 순간 없는게 더 나을 수도 있다.

2. 다중 버스 : CPU가 여러 개의 버스를 공유한다. 1:1 느낌 하지만 모든 버스가 사용중이면 기다려야 한다.

3. 크로스바 스위치 버스 : 교차 지점에 스위치를 갖다두어 물리적인 버스의 수를 줄였다.

4. 계층적 버스 : 로컬 버스(Local Bus와 시스템버스(Global bus)로 나누고 전용 메모리 처리기를 로컬 버스에 두고
커버가 안되는 메모리를 컴파일러가 배분하고 배치하게 된다

5. 다중 포트 메모리 : 예로 CPU -> VRAM -> GPU 를 들 수 있다. VRAM은 포트가 두개로 CPU와 GPU와의 버스 경쟁 없이
VRAM의 내용을 읽어서 모니터에 디스플레이할 수 있는 장점이 있다.
```

### 분산 처리 시스템(Distributed Computing Systems)
```
분산 처리 시스템은 독립된 시스템들이 버스가 아닌 네트워크로 연결되어 병렬 처리 환경을 제공한다.
분산 처리 시스템의 목적 및 효과로서 성능향상, 자원공유, 신뢰성 향상, 점진적 확장 등을 들 수 있다.
분산 처리 시스템은 위치 투명성, 접근 투명성, 고장 투명성, 중복 및 이동 투명성 등의 기능이 제공되어야 한다.
(어디 있는 지,중복인지, 이동이 되었는 지, 고장이 났는 지를 사용자는 그 내용을 인식할 필요가 없다는 뜻)
분산 처리 시스템은 네트워크로 연결되므로, 버스로 연결되는 강결합 시스템에 대비되는 개념으로
약결합 시스템 혹은 클러스터 시스템이라고 부른다.
분산 처리 시스템의 연결 형태에는 하이퍼 큐브, 완전 연결, 성형, 링형 등이 있다.
```

### 분산 처리 시스템의 연결 형태
```
1. 하이퍼 큐브 : 노드 간의 평균 거리가 짧고 경로 배정이 비교적 간단하다. 노드 하나의 연결된 노드 수를 n이라고 할 때 총 노드의 수는
2의 n승이 된다.

2. 완전 연결 : 모든 노드들이 직접 1:1 통신을 할 수 있도록 연결한 연결 형태이다. 사이트 간 통신 속도가 빠르고 연결 경로가 많아
통신 신뢰성이 높다는 장점이 있다. 하지만 초기 설치 비용과 확장 비용이 크다.

3. 성형 : 중앙에 중계 시스템을 두는 형태로 초기 설치, 확장이 쉽지만 중개 역할이 고장나면 안되서 신뢰성이 낮다.

4. 링형 : 성형 연결의 단점과 장점을 절충한 형태로 연결 반경이 좁고 새로운 노드 추가가 용히하나 두 개 이상의 노드가 다운되면 전체
네트워크가 양분된다.
```

## 컴퓨터의 주요 구성 요소
```
컴퓨터의 주요 구성 요소는 시스템 버스, 즉 어드레스 버스, 데이터 버스, 제어 버스 등 3 종류의 버스로 연결되어 있다.
```
