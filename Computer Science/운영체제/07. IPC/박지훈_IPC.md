### IPC (Inter Process Communication)
스레드와 달리 독립적인 메모리 공간을 가지고 있는 프로세스들이 통신을 할 수 있도록 하는 것이 IPC 통신이다.
프로세스는 커널이 제공하는 IPC 설비를 이용해 프로세스간 통신을 할 수 있게 된다.
커널은 하드웨어와 프로세스를 연결하는 인터페이스 역할을 한다고 생각하면 된다.

### IPC 종류
1. 익명 PIPE
  - 단방향 통신
  - 하나의 프로세스는 데이터 쓰고, 다른 하나는 읽기만 함
  - 누구랑 통신할 지 명확함
2. Named PIPE(FIFO)
  - 전혀 모르는 프로세스와 통신
  - 얘도 단방향 통신
3. Message Queue
  - 입출력 방식은 Named PIPE와 동일
  - 파이프 처럼 데이터 흐름이 아니라 메모리 공간이다.
  - 여러 프로세스가 동시에 데이터를 쉽게 다를 수 있다.
4. 공유 메모리
  - 파이프, 메시지 큐 == 통신 설비 <-> 공유메모리 == 데이터 자체 공유 설비
  - 프로세스간 메모리 영역을 공유해서 사용
  - 프로세스가 공유 메모리 할당을 커널에 요청하면, 커널은 해당 프로세스에 메모리 공간을 할당해주고 이후 모든 프로세스는 해당 메모리 영역에 접근 가능
  - 중개자 없이 메모리 접근 가능해서 빠름
5. 메모리 맵
  - 공유 메모리처럼 메모리 공유
  - 열린 파일을 메모리에 맵핑시켜서 공유하는 방식 (공유 매개체가 파일+메모리)
  - 주로 대용량 데이터 공유 시 사용
6. 소켓
  - 네트워크 소켓 통신을 통해 공유
  - 원겨겡서 프로세스 간 데이터를 공유할 때 사용
  - 서버 (bind, listen, accept), 클라이언트(connect)

이러한 IPC 통신에서 데이터를 동기화하고 보호하기 위해 세마포어와 뮤텍스를 사용.
