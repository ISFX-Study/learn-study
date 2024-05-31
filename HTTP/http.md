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

## 3. HTTP 메세지

![그림3](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcSUhhz%2FbtsHLYrqBpH%2FLnmWEkm5KJ8dh3k3oLPnnk%2Fimg.png)

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
     + 문구 : 짦은 상태 코드에 대한 설
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


#### 출처(참고문헌)
- GPT
- 웹의 기초
- HTTP웹 기본지식

#### 각주
