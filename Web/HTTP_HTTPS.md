### HTTP(HyperText Transfer Protocol)
- 인터넷 상에서 클라이언트와 서버가 자원을 주고 받을 때 쓰는 통신 규약
- 도청, 위장, 변조와 같은 보안 취약점이 있다.

<br>

### HTTPS(HyperText Transfer Protocol Secure)
- 클라이언트와 서버가 SSL 프로토콜을 사용해 암호화된 상태로 안전하게 자원을 주고받는 통신 규약

<br>

### HTTPS 통신 흐름
1. HTTPS 적용을 위해 서버는 공개키와 개인키 쌍을 만든다.
2. 신뢰할 수 있는 CA(Certificate Authority)와 계약하여 공개키 관리 및 인증서 발급을 요청한다.
3. CA는 서버의 공개키와 정보를 포함한 인증서에 전자서명을 하여 서버에 전달한다.
4. 서버는 이 인증서를 클라이언트에게 전달한다.
5. 클라이언트(브라우저)는 CA의 공개키로 인증서를 검증하고, 서버의 공개키를 얻는다.
6. 클라이언트는 핸드쉐이크 과정에서 난수를 조합해 pre-master-secret을 생성하고, 서버의 공개키로 암호화해 서버에 전송한다.
7. 서버는 자신의 개인키로 이 값을 복호화하여 동일한 pre-master-secret을 얻는다.
8. 양측은 pre-master-secret으로부터 master-secret을 만든다.
9. master-secret-key를 통해 session-key를 생성하고, 이를 이용해서 대칭키 암호화 방식으로 통신한다.
10. 각 통신 세션 종료 시 session-key는 폐기된다.
