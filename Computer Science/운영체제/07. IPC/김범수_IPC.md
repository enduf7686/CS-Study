## IPC

프로세스는 독립적으로 실행 된다.

하지만, **프로세스간 통신이 필요한 경우** 어떻게 해야하나? → 이럴 때 사용하는 것이 IPC 통신

IPC를 하는 방법은 **커널**을 통해 할 수 있다.

### 종류

1. PIPE (익명 PIPE)
    - 프로세스 두 개를 연결하고, 단방향으로 전송만 하면 되는 방식
    - 이게 `Half-Duplex(반이중)`
2. Named PIPE(FIFO)
    - 통신을 할 프로세스가 명확하지 않은 경우에서도 사용이 가능하다.
    - 부모 프로세스와 무관하게 모든 프로세스간 통신이 가능하다.
    - 하지만, 읽기/쓰기가 동시에 가능하지 ㅏㅇㄶ다.
3. Message Queue
    - Queue는 FIFO 방식의 설비
    - 방신은 Named PIPE와 동일하지만, 다른 점은 메모리 공간이라는 점이다.
    - 즉, 데이터를 전송하는 파이프와는 달리 적재된 메모리에서 데이터를 꺼낼 수 있는 방식으로 여러 개의 프로세스가 동시에 데이터를 쉽게 다룰 수 있다.
4. Shared Memory
    - 공유메모리가 데이터 자체를 공유하도록 지원하는 것
    - 통신과는 별개로 사용되는 것으로 Thread에서 처럼 프로세스간 메모리 영역을 공유해서 사용
    - 이는 중개자가 존재하지 않아 모든 IPC 중에 가장 빠르게 작동한다.
5. Memory Map
    - 공유 메모리와 비슷한 방식
    - 차이점은 열린 파일을 메모리에 맵핑시켜서, 공유한다는 점
6. Socket
    - 프로세서들 사이의 통신이 가능하게 하는 것으로
    - client와 server 단으로 나뉘어 `bind, listen, accept`를 통해 소켓 연결을 한 뒤 데이터를 주고받는 방식이다.

**Semaphore**

- 다른 IPC는 메시지 전송을 목적으로 하지만, 세마포어는 다르다.
- 프로세스 간 데이터를 동기화하고 보호하는 데 목적이 있다.
- 특정 데이터를 공유하게 될 경우 발생하는 동시 접근 문제를 막기 위한 것