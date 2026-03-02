### OAuth 2.0
- 제 3자 애플리케이션이 사용자의 비밀번호 없이도 제한된 권한으로 사용자 정보에 접근할 수 있도록 하는 인증/인가 프레임워크다.
- Resource Owner는 자원의 소유자다.
- Client는 사용자 정보에 접근하려는 애플리케이션이다.
- Authorization Server는 카카오, 구글 등의 인증 서버다.
- Resource Server는 실제 사용자 정보를 가지고 있는 서버다.
- Authorization Code Grant 방식이 가장 많이 사용된다.
- 예를 들어, 사용자가 카카오로 로그인 버튼을 누르면 카카오 로그인 페이지로 이동 ➡️ 사용자가 동의하면 인증 코드(Authorization Code) 발급 ➡️ 우리 서버가 이 코드로 Access Token을 받아 사용자 정보를 가져오는 흐름이다.
- JWT와 함께 사용하면 더욱 안정한 인증 시스템을 만들 수 있다.
