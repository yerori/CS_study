# 예영님 Yeyeong99

## 1. 서버와 클라이언트

### 의미
    1. 서버: 서비스를 제공하는 쪽
        1. 웹서버: 웹사이트를 제공하는 서버로 만들어줌.
            1. ex) 아파치 NginX
    2. 클라이언트: 서비스를 제공받는 쪽

### request - response
    
    : 클라이언트가 먼저 서버에 요청을 보내고 서버가 그에 따른 응답을 클라이언트에 보냄.
    
    >💡 **무상태 프로토콜(stateless)**   
    클라이언트가 서버에 요청하기 전에 먼저 서버와 연결을 함. 그리고 응답이 끝난 이후엔 연결을 바로 끊음. 이러한 이유로 클라이언트가 새로운 요청을 보낸다고 해도, 서버는 그 클라이언트가 이전에 요청을 보냈던 클라이언트인지 모름.  
     1️⃣ 장점  
    ➖ 불특정 다수를 대상으로 하는 서비스에 적합함.  
    ➖ 클라이언트와 서버가 계속 연결을 유지하는 것이 아니기 때문에 클라이언트와 서버 간의 최대 연결 수보다 많은 요청과 응답을 처리할 수 있음  
       2️⃣ 단점  
    ➖ 연결을 끊어버려 클라이언트의 이전 상황을 알 수 없음.
    → 이를 위해 cookie 이용
    
    1. request
        1. 요청 데이터 포멧: HTTP 요청 메세지 ⇒ 요청 헤더, 빈 줄, 요청 바디로 나뉨
            1. 헤더: GET - 요청 매서드, GET은 요청 바디에 내용이 없음
                1. 요청 URI, 프로토콜 버젼
                - GET : 정보를 요청하기 위해서 사용한다. (SELECT)
                - POST : 정보를 밀어넣기 위해서 사용한다. (INSERT)
                - PUT : 정보를 업데이트하기 위해서 사용한다. (UPDATE)
                - DELETE : 정보를 삭제하기 위해서 사용한다. (DELETE)
                - HEAD : (HTTP)헤더 정보만 요청한다. 해당 자원이 존재하는지 혹은 서버에 문제가 없는지를 확인하기 위해서 사용한다.
                - OPTIONS : 웹서버가 지원하는 메서드의 종류를 요청한다.
                - TRACE : 클라이언트의 요청을 그대로 반환한다. 예컨데 echo 서비스로 서버 상태를 확인하기 위한 목적으로 주로 사용한다.
    2. response 응답
        1. 빈줄 다음 응답 내용이 옴
    

## 2. 웹서버

보통 소프트웨어를 의미하지만, 웹서버 소프트웨어가 동작하는 컴퓨터를 지칭하기도 함.

### 종류
    
    아파치, NginX가 대표적
    
    <aside>
    💡 아파치와 NginX 차이
    ✅ 작동 방식에서 근본적인 차이
    ✅ 사용되는 부분
    아파치 - 다중 프로세스, 다양하고 검증된 서비스
    NginX -  이벤트로 처리, 성능과 가벼움을 중시하는 서비스  
    
### 역할

- 정적 웹: 서버 컴퓨터에 있는 특정 폴더를 개방, HTML등 필요한 파일에 접근, 클라이언트가 요청하는 HTML, 등 각종 리소스를 제공
    
    ex) 웹브라우저가 www.naver.com이라는 웹서버에 접속 ⇒ 웹서버는 웹브라우저에 HTML 문서와 함께 여러 리소스를 보냄. ⇒ 웹 브라우저는 이를 해석한 후 조합, 즉 렌더링을 진행한 후 화면에 출력
    
- 웹브라우저, 웹크롤러(다른 웹사이트 정보를 읽어갈 때 사용하는 웹 소프트웨어)가 요청하는 리소스는 컴퓨터에 저장되어 있는 정적 데이터(이미지, js, css, html 파일 등)이거나 동적인 결과(프로그램을 통해서 만들어진 결과)가 될 수 있음


## 3. WAS

- 쓰임
    
    자바, JSP로 만든 웹 또는 API 어플리케이션을 실행할 때 Web Application Server가 사용
    
- 종류
    
    톰캣: 스프링으로 코딩 시 사용
    

미들웨어의 일종. 웹어플리케이션이 동작하도록 지원하는 목적을 가지고 있음.


>💡 **미들웨어**  
DBMS(데이터베이스 관리 시스템)에 클라이언트가 직접 접속하는 것에서 많은 문제가 파생 되어 발명됨(ex - 보안상의 문제, 업데이트 문제)  
👍 장점  
클라이언트는 입,출력만 담당하게 되고 크기가 작아짐. 
프로그램 로직이 변경되어도 모든 클라이언트를 재배포할 필요없이 미들웨어만 변경하면 됐음.

## 4. 웹서버와 WAS의 차이점

1. 정적 vs 동적
2. 성능 상 큰 차이가 없지만 규모가 커질 수록 웹서버와 WAS를 분리

### 웹 서버의 기능 
- 보안
    reverse proxy: 이용자들에게 서버의 정보, 즉 내부 구조를 숨김.
- 로드 밸런싱  
    WAS 이용의 균형을 맞춰줌. 여러 이용자가 몰리면 분산해주는 역할.    
- 캐싱    
    서버를 이용하는 사람들이 자주 찾는 걸 모아두고 필요 시 바로 제공
    
### 장애극복기능(failover)  
-> WAS가 오작동 해 웹서버 자체에서 WAS에 대한 접근을 막을 수 있음.