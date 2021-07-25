# Authentication



### Sesstion Based Authentication

- 사용자가 로그인을 하면 session에 sessionid를 저장하고 응답과 요청에 sessionid를 쿠키에 넣어 같이 보낸다.



### Token Based Authentication

#### JWT(JSON Web Token)

- JSON 포맷을 활용하여 정보를 교환하기 위한 표준 포맷
- JWT 자체가 필요한 정보를 모두 갖기 때문에 이를 검증하기 위한 다른 검증 수단이 필요 없음
- Session에 비해 상대적으로 HTML, HTTP 환경에서 사용하기 용이
  - Session은 유저의 session 정보를 서버에 보관해야 한다.
  - JWT는 Client Side에 토큰 정보를 저장하고 필요한 요청에 같이 넣어 보내면 그 자체가 인증 수단이 된다.
- 높은 보안 수준
- 서버 메모리에 정보를 저장하지 않으므로 서버의 자원을 절약할 수 있다.
- 사용자가 로그인을 하면 서버에서 JWT를 발급하여 client에게 보내주고 이후부터는 서버에 요청을 보낼 때 JWT를 같이 보내준다.



#### JWT 구조

##### Header

- 토큰의 유형과 Hashing algorithm

##### Payload

- 토큰에 넣을 정보
- Registered claims
- public claims
- private claims

##### Signature

- Header와 Payload의 encoding 값을 더하고 거기에 private key로 hashing하여 생성



