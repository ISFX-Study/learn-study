---
created: 2024-05-11
title: HTTP
author: pej
category: study
tag: study
aliases: []
---

## 1. HTTP(Hypertext Transfer Protocol)
  + 정의
    + **인터넷에서 데이터를 주고 받는데 사용되는 프로토콜**
    + 클라이언트(웹브라우저)와 서버에서 사용
    + 클라이언트(일반적으로 웹 브라우저)가 서버에 요청을 보내면, 서버는 해당 요청에 대한 응답을 반환하는 형태. 이러한 요청과 응답은 일련의 텍스트 기반 메시지로 구성되어 있음
 
  + 특징
    + **클라이언트-서버 구조**
      ![클라이언트서버](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcN9XsH%2FbtsHmRN2oKH%2FPGi7Bv8VJL3aKVRBrggoE1%2Fimg.png)
    + **Stateless**
      + 서버가 클라이언트의 상태를 보존하지 않음
    + 비연결성
      + 한 번의 요청에 대한 응답이 완료되면 연결은 닫히게 됨
      + 이러한 문제를 개선하기 위해서 파이프라이닝 기능이 나옴
    
## 2. HTTP 역사
  + HTTP의 탄생(1989)
    + 월드 와이드 웹(WWW)의 핵심 프로토콜로 개발
  + HTTP/0.9(1991)
    + GET 메서드만 지원
  + HTTP/1.1(1996)
    + 첫 번째 공식 표준
    + 여러 메서드(GET, POST, HEAD, 등)와 헤더, 상태 코드(200 OK, 404 Not Found 등) 등이 추가되었음
  + **HTTP/1.1(1999)**
    + 지속적인 연결(Persistent Connection)  
      ![그림1](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbfS0kQ%2FbtsHnHcD1FG%2FbxQiH1ZYFDtj9hrhkKNk5k%2Fimg.png)
      ![그림2](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FlNQpI%2FbtsHk2pEAH4%2F11wemQT5lH5OSqP0aUVE1k%2Fimg.png)
      
   + 파이프라이닝(Pipelining)
      + 기본적으로 HTTP는 요청과 응답이 순차적으로 이루어지기 때문에 클라이언트는 이전 요청의 응답을 받기 전까지 다음 요청을 보낼 수 없었음
      + 클라이언트 여러 요청을 보내면 서버에서 순서대로 여러 응답을 보낼수 있음
   + 캐시 관리 기능 추가
   + 웹 페이지의 로딩 속도와 성능이 향상
  + HTTP/2(2015)
    + 이진 형식으로 데이터 전송
    + 별도의 TCP 연결을 맺어야 했지만, 스트림을 통한 다중화
  + HTTP/3(2018)
    + TCP 대신 UDP 프로토콜 사용
    + 모든 웹사이트와 브라우저에서 HTTP/3가 지원되는 것은 아님(현재 구글은 적용되어 있음)

  > 파이프라이닝 VS 스트림을 통한 다중화
  > + 파이프라이닝 : 요청 순서대로 응답을 반환해야함
  > + 스트림을 통한 다중화 : 각각의 스트림 안에서 병렬로 HTTP 요청 및 응답이 이뤄지면서 대기 상태가 없어짐  
    
![그림3](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FUR49F%2Fbtsc2XWUt0l%2FLGEpLnaRI1lB2MtQf4pkl0%2Fimg.png)

## 3. HTTP 메서드
+ HTTP 메서드의 종류
  + GET
    + 리소스 조회
    + 쿼리 파라미터를 통해서 데이터 전달
  + POST
    + 요청 데이터 처리
    + 메시지 바디를 통해서 데이터 전달
    + 새로운 리소스를 생성하고, 그 리소스의 위치(URI)를 반환
    ```
    POST /users
    ```
  + PUT
    + 리소스를 완전히 대체, 없으면 생성
    + 수정할 리소스를 알고 있어서 리소소를 완전히 대체 할 수 있음
    ```
    PUT /users/123
    ```
  + PATCH
    + 리소스를 부분 변경
  + DELETE
    + 리소스를 삭제
+ HTTP 메서드의 속성
## 4. HTTP 상태코드


## 5. HTTP 메세지

![그림3](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcSUhhz%2FbtsHLYrqBpH%2FLnmWEkm5KJ8dh3k3oLPnnk%2Fimg.png)

+ HTTP 요청 메세지
```
POST /submit-form HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.3
Content-Type: application/x-www-form-urlencoded
Content-Length: 27
Connection: keep-alive

username=example&password=1234
```
+ HTTP 응답 메세지 
```
HTTP/1.1 200 OK
Date: Mon, 31 May 2024 12:00:00 GMT
Server: Apache/2.4.41 (Ubuntu)
Content-Type: text/html; charset=UTF-8
Content-Length: 138
Connection: keep-alive

<html>
<head>
    <title>Example Page</title>
</head>
<body>
    <h1>Hello, World!</h1>
    <p>This is an example page.</p>
</body>
</html>
```

+ 구성
  + **시작 라인(요청 라인/ 상태 라인)**
    + 요청
      + HTTP 메서드 : GET, POST 등등
      + 요청 대상(request-target) : 요청할 리소스의 경로
      + HTTP 버전 : 사용 중인 HTTP 프로토콜의 버전
      ```
      GET /index.html HTTP/1.1
      ```
    + 응답 
      + HTTP 버전 : 사용 중인 HTTP 프로토콜의 버전
      + HTTP 상태코드 
      + 문구 : 짦은 상태 코드에 대한 설명
      ```
      HTTP/1.1 200 OK
      ```
  + **헤더**
    + **HTTP 전송에 필요한 모든 부가정보**
    + 각 헤더는 `filed: value` 형식으로 여러개가 있을수 있으며, 각 헤더는 개행 문자(CRLF)로 구분됨
    + filed는 대소문자를 구분하지 않으나 value은 대소문자를 구분함
    ```
    Host: www.example.com
    User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.3
    Accept-Language: en-US,en;q=0.9
    ```
  + **CRLF**
    + 헤더 섹션의 끝을 표시하는 것으로 반드시 있어야 함
  + **본문(Body)**
    + GET 요청시에서는 본문이 없음
    + **실제 전송할 데이터**

## 6. HTTP 헤더
  + 구성
    ![그림5](https://developer.mozilla.org/ko/docs/Web/HTTP/Messages/http_request_headers3.png)

    + 일반 헤더(General Headers)
      + 요청과 응답 메세지 전체에 적용되는 정보가 있는 헤더
    + 요청 헤더(Request Headers)
      + 클라이언트가 서버에 요청을 보낼 때 사용되는 헤더
    + 응답 헤더(Response Headers)
      + 서버가 클라이언트에게 응답을 보낼 때 사용되는 헤더
    + 표현 헤더(Representation Headers)
      + 메시지 본문에 대한 표현을 기술하는 헤더
    
+ **콘텐츠 협상(Accept)**
  + **클라이언트와 서버간의 리소스 의사결정 과정**
  + 표현 헤더에 안에 들어감
  + Content-Type
      + 표현 데이터의 데이터 타입
      ```
      application/json 
      charset=utf-8
      ```
  + Content-Encoding
    + 표현 데이터의 인코딩
      + 요청하는 곳에서 압축후 인코딩 헤더 추가, 응답에서 인코딩 헤더의 정보로 압축 해제
      ```
      gzip
      ```
  + Content-Language
    + 표현 데이터의 자연언어
    ```
    ko
    en
    en-US
    ```
  
+ **쿠키**  
  ![그림6](https://velog.velcdn.com/images%2Furtimeislimited%2Fpost%2F4cecd1b4-45c8-4cec-b9c7-33519669d421%2Fimage.png) 
  ![그림7](https://velog.velcdn.com/images%2Furtimeislimited%2Fpost%2Fe94c56ce-3d9c-40ca-a2a8-59784153972c%2Fimage.png)
    
  + **Set-Cookie** : 서버에서 클라이언트로 쿠키 전달
  + **Cookie**: 클라이언트가 서버에서 받은 쿠키를 저장, HTTP 요청시 서버로 전달
  + 사용자 로그인 세션관리, 광고 정보 트래킹에 사용됨
  + 네트워크 트래픽을 유발 할 수 있으므로 최소한의 정보만 사용하는게 좋음
  + 서버를 통하지 않고 웹 브라우저 내부에 저장하고 싶으면 웹스토지(localStorage, sessionStorage)를 이용하는 방법도 있음
  + 생명주기
    ```
    Set-Cookie: expries=날짜 // 만료일이 되면 쿠키 삭제됨
    Set-Cookie: max-age=3600(3600초) // 0이나 음수를 지정하면 쿠키 삭제됨
    ```
    + 세션 쿠키 : 만료 날짜를 생략하면 브라우저 종료될때 삭제됨
    + 영속 쿠키 : 만료 날짜를 입력하면 해당 날짜까지 유지(브라우저 종료되도 유지됨)
    
+ 일반 정보
   + referer
      + 이전 웹페이지 주소
      + 유입 경로를 분석 할때 사용함
      + 요청에서 사용함
   + User-Agent
       + 클라이언트 애플리케이션 정보
       + 요청에서 사용함
   + Server
      + 요청을 처리하는 원래 서버의 정보
   + Host
     + 요청한 도메인의 정보
     + 헤더 정보중에 필수값임

## 7. HTTP 헤더 - 캐시와 조건부 요청
+ HTTP 캐싱
    + **리소스를 저장하여 다시 동일한 리소스를 요청할 때 더 빠르게 제공하는 기술**
    + 사용자 응답 속도 향상
    + 서버의 부하 완화

+ 캐시 방식
  + 시간 기반
    + 유효한 시간을 비교하는 방법
    + 특정 시간 동안만 유효하다는 것을 의미
    + `max-age`속성을 이용
    ```
    Cache-Control: max-age=60
    ```
    + 검증 순서
    ```
    1. 서버가 클라이언트에게 응답할 때, `Last-Modified` 속성으로 수정일을 응답함
    2. 응답받은 브라우저는 캐싱을 시작
    3. 다시 서버가 클라이언트에게 재요청하면서, `If-Modified-Since` 속성에 수정일을 넣음 
    4. 서버는 데이터가 변경 되었으면 다시 전달하고, 변경 되지 않았다면 변경되지 않았다는 응답(304 Not Modified)을 줌
    ```
  + 내용 기반
    + 파일 자체를 비교하는 방법
    + 시간 기반 캐시 방식을 보완하기 위해서 나옴
    + `ETag(Entity Tag)`
        + 캐시용 데이터에 임의의 버전을 명시
        + 데이터가 변경될때마다 버전을 변경함
    + 검증 순서
    ```
    1. ETag 같으면 유지, 다르면 데이터를 다시 받기
    ```
    
+ 캐시 제어 헤더
  + **Cache-Control**
    + max-age
    + no-cache
      + 조건부 요청을 이용해서 항상 유효한 데이터인지 체크함
      + `max-age=0`와 같은 뜻
    + no-store
      + 데이터를 저장하지 말라는 뜻

+ 조건부 요청과 검증 헤더
  + 조건부 요청 헤더 : 요청 헤더에서만 사용 가능
  + 검증 헤더 : 응답 헤더에 사용

  |구분|조건부 요청 헤더|검증 헤더|
  |------|---|---|
  |시간 기반|If-Modified-Since, If-Unmodified-Since|Last-Modified|
  |내용 기반|If-Match, If-None-Match|ETag|

+ 캐시 무효화

#### 출처(참고문헌)
+ GPT
+ 웹의 기초
+ 모든 개발자를 위한 HTTP 웹 기본 지식
+ https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Cache-Control
+ https://jeonghwan-kim.github.io/2024/02/08/http-caching

#### 각주
