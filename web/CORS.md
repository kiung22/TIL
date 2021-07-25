## CORS

### Same-origin policy(SOP)

- 동일 출처 정책
- 특정 출처에서 불러온 문서나 스크립트가 다른 출처에서 가져온 리소스와 상호작용하는 것을 제한하는 보안 방식
- URL의 Protocol, Port, Host가 모두 같아야 동일한 출처이다.
  - http의 포트는 80이 기본값



### Cross-Origin Resource Sharing(CORS)

- 교차 출처 리소스 공유
- 추가 HTTP header를 사용하여 특정 출처에서 실행중인 웹 애플리케이션이 다른 출처의 자원에 접근할 수 있는 권한을 부여하도록 부라우저에 알려주는 체제
- 리소스가 자신의 출처(Domain, Protocol, Port)와 다를 때 교차 출처 HTTP 요청을 실행
- 다른 출처의 리소스를 불러오려면 그 출처에서 올바른 CORS header를 포함한 응답을 반환해야한다.



### Access-Control-Allow-Origin 응답 헤더

- 리소스를 공유할 촐처를 설정
- `*` 이면 모든 출처를 허용한다는 의미



1. Vue.js에서 서버로 요청
2. 서버는 Access-Control-Allow-Origin에 특정한 origin을 포함시켜 응답
3. 브라우저는 응답에 Access-Control-Allow-Origin을 확인한 후 허용 여부를 결정
4. 프레임워크 별로 이를 지원하는 라이브러리가 존재
   - django는 django-cors-headers를 통해 응답 헤더 및 추가 설정 가능

