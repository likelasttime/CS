|TCP 3 Way-Handshake|TCP 4 Way-Handshake|
|-------------------|-------------------|
|클라이언트는 서버에 요청을 전송할 수 있는지, 서버는 클라이언트에 응답을 전송할 수 있는지 확인하는 과정|클라이언트는 서버에게 연결해제를 통지하고, 서버가 이를 확인하고 클라이언트에게 받았음을 전송하고 최종적으로 연결 해제|

<br>

### TCP 3 Way-Handshake
- `SYN(Synchronize Sequence Numbers)`, `ACK(Acknowledgment)` 패킷을 주고 받는다.
- Client는 Server에 접속을 요청하는 `SYN` 패킷을 전송한다. Client는 `SYN`을 보내고 `SYN/ACK` 응답을 기다리는 `SYN_SENT` 상태가 된다.
- Server는 `SYN` 요청을 받고 Client에게 요청을 수학한다는 `ACK`와 `SYN flag`가 설정된 패킷을 발송하고 Client가 `ACK`로 응답하기를 기다린다. Server는 `SYN_RECEIVED` 상태다.
- Client는 Server게 `ACK`를 보내고 난 뒤에 연결이 이루어진다. Server의 상태는 `ESTABLISHED`다. 

<br>

### TCP 4 Way-Handshake
- 혹시 패킷이 나중에 도착할까봐 서버에서 소켓이 닫혔다고 통지해도 클라이언트 측에서는 일정시간을 대기한다. `TIME_WAIT` 상태다. Server가 `FIN`을 전송하기 전에 전송한 패킷이 `Routing` 지연이나 패킷 유실로 인한 재전송 등으로 `FIN` 패킷보다 늦게 도착하는 상황이 생길 수 있기 때문이다.
- Client가 연결을 종료한다는 `FIN` 플래그를 전송한다.
- Server는 확인 메시지를 보내고 자신의 통신이 끝날 때까지 기다린다. `TIME_WAIT` 상태다.
- Server가 통신이 끝났으면 연결이 종료되었다고 Client에게 `FIN` 플래그를 전송한다.
- Client는 확인했다는 메시지를 보낸다.
