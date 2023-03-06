# RESTAPI 만들기

### 예상 시나리오
1. jwt토큰 없이 api를 호출하였을 경우
2. 형식에 맞지 않거나 만료된 jwt토큰으로 api를 호출한 경우
3. jwt토큰으로 api를 호출하였으나 해당 리소스에 대한 권한이 없는 경우

1.커스텀 예외 처리가 적용 안되는 이슈 발생
- SpringSecurity에서 예외 처리 필터링이 앞단에서 먼저 되기 때문에 의도한 시나리오의 예외가
전달 되지 않는다(DispatcherServlet)
  해결방법 : SpringSecurity에서 제공하는 AuthenticationEntryPoint를 상속받아 재정의 필요