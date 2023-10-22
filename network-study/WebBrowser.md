# 웹 브라우저가 메세지를 만든다

## 목차
1. [HTTP 리퀘스트 메세지 작성](#HTTP-리퀘스트-메세지-작성)

## HTTP 리퀘스트 메세지 작성

- URL
  - 네트워크 상에서 자원의 위치를 알리기 위한 규약
  - 도메인명, 경로, 포트번호 등 쓸 수 있음
  - 모든 URL은 맨 앞 문자열에 액세스 프로토콜을 포함함
    - 프로토콜 : 통신 동작의 규약
    - `http:`: 웹 서버, `FTP:`: FTP(파입 업/다운로드) 서버, `mailto:` 메일 ··· etc.

### 브라우저는 URL을 해독한다.
#### URL의 요소
  - `http:` + `\\` + `웹 서버명` + `/` + `디렉토리` + `/` + ··· + `파일명`
  - ✔️ **파일명** 생략 가능
    -  eg) `http://example.com/test/`
    - 서버에 미리 정의해야 함. (대체로 index.html)
  - ✔️ **디렉토리명** 생략 가능
    - eg) `http://example.com`
    - 루트 디렉토리에 미리 설정된 파일에 엑세스
  - ❔`/` 가 없는 경우엔?
    - eg) `http://example.com/test`
      - test라는 디렉토리가 있으면 디렉토리로, 파일이 있으면 파일로 간주함
        - 둘 다 있을 수 없음

### HTTP의 기본 개념
#### HTTP 프로토콜 
  - 클라이언트와 서버가 주고받는 메세지의 내용이나 순서를 정한 것
  - 클라이언트 → 서버 
    - 리퀘스트 메세지를 보냄
      - URI, METHOD
  - 서버 → 클라이언트
    - 응답 메세지를 보냄
      - Status Code
#### Request Message
  - Request Line
    - METHOD
      - GET, POST, PUT, DELETE ··· etc.
    - URI
    - HTTP 버전
  - 메세지 헤더
    - 요청의 부가적인 정보
      - 데이터의 종류, 날짜 ··· etc.
  - 메세지 본문
    - 메소드와 URI만으로 요청을 보낼 수 있는 경우엔 메세지 본문이 없을 수도 있음
#### Response Message
  - Status Line
    - HTTP 버전
    - Status Code
    - | code | desc      |
      |------|-----------|
      | 1XX  | 처리의 경과 상황 |
      | 2XX  | 정상 종료     |
      | 3XX  | 다른 조치 필요  |
      | 4XX  | 클라이언트 오류  |
      | 5XX  | 서버 오류     |

    - Status Message
      - OK, NOT FOUND ··· etc.
  - 메세지 헤더
  - 메세지 본문
    - `Content-Type: text/html`인 경우에 html 태그가 포함될 수 있음
      - 태그 안에 영상/사진 파일이 포함되어 있다면 브라우저는 파일을 읽기 위한 Request를 웹 서버에 보내게 됨.
        - 예를 들어 하나의 응답 메세지에 세 개의 사진이 포함되어 있다면 브라우저는 총 4번의 요청을 보내게 되는 것.