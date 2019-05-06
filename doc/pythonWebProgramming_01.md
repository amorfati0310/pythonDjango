## 01 ~03 
파이썬 웹 프로그래밍 책 보고 3장까지 보고 정리하기 :D 

## 웹 프로그래밍ㅇ의 이해 

HTTP(s) 프로토콜로 정보를 주고 받으며 
사용자에게 웹 컨텐츠를 제공하는 것 

* 클라이언트-서버 
요청하는 쪽을 클라이언트 
제공하는 쪽을 서버라고 한다. 

```
웹 클라이언트 -> 웹서버 
           <-  

```
웹클라이언트: 브라우저, 스크립트...
웹서버: (웹 프레임워크 사용하여 개발 하는 경우가 웨많음)

브라우저, 컬, telnet, custom library등 다양한 요청방식 있다.  

### HTTP 프로토콜 

웹에서 서버-클라인트가 데이터를 주고 받기 위한 규약 
tcp/ip 프로토콜 위에서 동작 

hypertext 전송용 프로토콜이지만 여러 파일들을 전송할 수 있다. 

### 메시지 
요청 응답 메시지를 주고 받는다.
request message 
response message 

HTTP 메시지 구조 
```
스타트 라인 - 요청 | 상태라인 
헤더         
빈줄    CRLF 이걸 통해서 헤더/바디 구분
바디

헤더와 바디는 생략 가능하고 
바디에는 binaryData도 들어갈 수 있다.
```

첫번째 줄 요청 라인은 

```
메소드 프로토콜:host:포트번호/path/

```
#### 요청 메시지 

GET/ /book/shakesphere/ HTTP1.1
HOST: www.example.com:8000

#### 응답 메시지 

프로토콜 상태코드 상태 텍스트

#### HTTP 메소드 종류 

GET, POST, PUT, DELETE, HEAD, OPTIONS, TRACE, CONNECT 

GET, POST 주로 쓴다 

GET: 읽고,
POST: 정보를 새로 전달할 떄  

PUT, PATCH 일부만 수정할 때 PATCH 
PUT에 있는 data를 가지고 온전히 바꿔줄 떄 PUT 

CRUD(POST,GET,PUT,DELETE)

#### 상태코드 

1xx 정보제공
2xx 성공
3xx 리다이렉션 
4xx 클라이언트 에러 
5xx 서버 에러 

200 OK 
201 생성 
202 허용됨 
203 Non-authoriative information 
204 No content
205 Reset Code
301 url 변경 
302 Found url 일시적 변경 
303 See Other 다른 위치로 요청하라 
304 Not Modified 수정되지 않아서 캐시버전으로 사용해라 :ㅇ
307 임시로 리다이렉션 요청 필요 
400 잘못된 요청 
401 권한 없음 
403 금지됨 액세스 금지 
404 Not Found 찾을 수 없음 
500 내부 서버 오류 서버쪽에서 에러 발생 
502 프록시 역할 하는 서버에서 잘못된 응답을 받았다. 
503 서비스 제공불가 서버 과부하,점검 등으로 서버에서 서비스를 제공할 수가 없다. 


#### URL 설계 
```
http://www.example.com:80/services?category=3kind=patents#n10
url스킴: 호스트명:포트번호/경로/쿼리스트링 프래그먼트

```

#### REST | GraphQL 

> Rest 

* 모두 리소스로 바로보는 형식

http메소드로 구분

> GraphQL

query realtion 설정으로 필요한 요청만 가지고 오는 방식

* endpoint 하나 
* Overfetching 
* Underfetching 방지 

#### 파이썬에서 URL 

간편 url(?,=,&,# 쿼리스트링등을 줄인 url) 및 정규표현식을 추가적으로 사용할 수 있습니다.

```
urlpatterns = [
  path('articles/<int:year>', views.year.arhive)
],
re_path(r'^articles/(?P<year>[0-9]{4}/$'), views.year.archive)
```

###  웹 어플리케이션 서버 

웹 서버 - 주로 정적파일 html, image, css, js파일을 웹 클라이언트에게 제공할 떄 웹 서버를 사용합니다. 동적인 처리는 주로 웹 어플리케이션 서버에서 담당합니다 

대표 프로그램 : Apache, Nginx 

웹 어플리케이션 서버: 동적 요청 처리하고 그 결과를 웹 서버로 반환합니다. 프로그램 실행과 데이터 베이스 연동 등을 처리 

대표프로그램: TomCat, JBoss,

동적 페이지는 -> 누가 언제 어떻게 요청했느냐에 따라 다르게 표현 되는 페이지 

파이선 웹 어플리케이션 서버: mod_wsgi, uwsgi, gunicorn

```
웹 클라이언트 <->웹서버 <-> 웹어플리케이션 서버 <->DB


웹서버: 정적 페이지 및 캐시 , 프록시 기능 등 추가적 수행 
제한 및 처리, 프로세스의 관리,인증제어, 암호화 처리 , 등을 처리한다. 
웹 어플리케이션 서버 

Hw 측면에서는 L4/L7 스위치 및 프록시 등의 도입을 고려하여 구성 

```