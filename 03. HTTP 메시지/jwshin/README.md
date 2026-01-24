# 03. HTTP 메시지

## 3.1 메시지의 흐름

- HTTP 메시지는 HTTP 애플리케이션 간에 주고받는 데이터의 블록들이다.
- 이 데이터의 블록들은 메시지의 내용과 의미를 설명하는 텍스트 메타 정보로 시작하고 그 다음에 선택적으로 데이터가 올 수 있다.

### 3.1.1 메시지는 원 서버 방향을 인바운드로 하여 송신된다

- HTTP 메시지는 **방향성**을 가진다.
- 클라이언트 → 서버로 가는 요청은 **인바운드**
- 서버 → 클라이언트로 가는 응답은 **아웃바운드**
    
    <img width="623" height="285" alt="image" src="https://github.com/user-attachments/assets/4f5b0dc1-2f0e-4a70-ade6-d07441b64413" />
    

### 3.1.2 다운스트림으로 흐르는 메시지

- HTTP 메시지는 **항상 다운스트림 방향**으로 흐른다.
- 요청 메시지냐 응답 메시지냐에 관계없이 모든 메시지는 다운스트림으로 흐른다.
- 요청
    - 클라이언트 → 프락시 → 서버
- 응답
    - 서버 → 프락시 → 클라이언트
        
        <img width="630" height="528" alt="image" src="https://github.com/user-attachments/assets/ec405465-087a-41c6-acd0-9517eef3e324" />
        

## 3.2 메시지의 각 부분

- HTTP 메시지는 **단순한 텍스트 기반 구조**
- 크게 세 부분으로 구성된다.
    - 시작줄
    - 헤더
    - 본문(선택)
        
        <img width="626" height="205" alt="image" src="https://github.com/user-attachments/assets/92b21632-fdd3-4a3a-aaa2-d528ebf39363" />
        

### 3.2.1 메시지 문법

- 모든 HTTP 메시지는 요청 메시지 또는 응답 메시지로 분류된다.
    
    <img width="626" height="330" alt="image" src="https://github.com/user-attachments/assets/2b7027ef-9ddb-45f1-9183-df717ff1964d" />
    
- 요청 메시지 형식
    - `<메서드> <요청 URL> <버전>`
    - `<헤더>`
    - `<엔티티 본문>`
- 응답 메시지 형식
    - `<버전> <상태 코드> <사유 구절>`
    - `<헤더>`
    - `<엔티티 본문>`

### 3.2.2 시작줄

- 모든 HTTP 메시지는 시작줄로 시작한다.
- 요청 메시지의 시작줄은 무엇을 해야 하는지 말해준다.
- 응답 메시지의 시작줄은 무슨 일이 일어났는지 말해준다.

### 요청줄

- 서버에게 **무엇을 할지** 요청
- 구성 요소
    - 메서드
    - 요청 URL
    - HTTP 버전

### 응답줄

- 요청 처리 결과를 전달
- 구성 요소
    - HTTP 버전
    - 상태 코드
    - 사유 구절

### 메서드

- 서버에게 수행을 요청하는 동작
- 주요 메서드
    - GET: 리소스 조회
    - HEAD: 헤더만 조회
    - POST: 서버가 처리해야 할 데이터 전송
    - PUT: 리소스 생성 또는 수정
    - DELETE: 리소스 삭제
    - TRACE: 요청 경로 추적
    - OPTIONS: 지원 메서드 조회
- 서버가 모든 메서드를 반드시 구현할 필요는 없다.

### 요청 URL

- 요청 대상 리소스를 식별
- 완전한 URL 또는 경로 형식
- 서버는 Host 헤더를 통해 실제 대상 서버를 인식

### 버전

- 메시지에서 사용 중인 HTTP 버전
- 형식
    - HTTP/메이저.마이너
- 버전은 **분수처럼 비교하지 않는다**
    - HTTP/2.22 > HTTP/2.3 (잘못된 비교)

### 상태 코드

- 요청 처리 결과를 나타내는 세 자리 숫자
- 첫 번째 자릿수는 분류 의미
    - 1xx 정보
    - 2xx 성공
    - 3xx 리다이렉션
    - 4xx 클라이언트 오류
    - 5xx 서버 오류

### 사유 구절

- 상태 코드를 사람이 읽기 쉽게 설명
- 애플리케이션 로직에는 영향 없음
- 클라이언트는 사유 구절이 달라도 같은 상태 코드면 동일하게 처리해야 한다.

### 3.2.3 헤더

- 시작줄 다음에 위치
- 이름 값 쌍 구조
- CRLF로 줄 구분
- 헤더 블록 끝은 **빈 줄(CRLF)**

### 헤더 분류

- 일반 헤더
- 요청 헤더
- 응답 헤더
- 엔티티 헤더
- 확장 헤더

### 3.2.4 엔터티 본문

- 메시지의 **선택적 데이터 영역**
- 텍스트 또는 바이너리 데이터 가능
- 메시지 본문이 없는 경우도 많다.
- 헤더와 본문은 **빈 줄로 구분**

### 3.2.5 버전 0.9 메시지

- HTTP의 초기 버전
- 요청은 오직 메서드와 요청 URL만 가진다.
- 응답은 오직 엔터티로만 되어 있다.
- 상태 코드, 헤더가 포함되어 있지 않다.
- 현재는 거의 사용되지 않지만 호환성 때문에 설명한다.

## 3.3 메서드

### 3.3.1 안전한 메서드(Safe Method)

- 서버에 **부작용을 일으키지 않는 메서드**
- 대표적으로
    - GET
    - HEAD
- 안전하다는 것은 HTTP 요청의 결과로 인해 서버에서 일어나는 일이 없다는 의미이다.
- 서버 구현에 따라 실제 부작용이 없다는 보장은 없다.

### 3.3.2 GET

- 가장 일반적인 메서드
- 서버에게 리소스를 요청하기 위해 쓰인다.
- HTTP/1.1 서버는 반드시 지원해야 한다.
    
    <img width="625" height="283" alt="image" src="https://github.com/user-attachments/assets/67c1d02d-d084-4f4e-bb51-5dd56a1ac85f" />
    

### 3.3.3 HEAD

- GET과 동일하게 동작
- 서버는 응답으로 헤더만을 돌려준다.
- 엔터티 본문은 결코 반환되지 않는다.
- 용도
    - 리소스 존재 여부 확인
    - 메타데이터 확인(타입 등)
    - 리소스 변경 여부 검사
        
        <img width="614" height="258" alt="image" src="https://github.com/user-attachments/assets/776a7793-cf5a-4ba9-8057-5a2681521350" />
        

### 3.3.4 PUT

- 요청 URL 이름으로 리소스를 생성하거나 수정
- 인증이 필요한 경우가 많음
    
    <img width="619" height="349" alt="image" src="https://github.com/user-attachments/assets/bb9a883b-1fb5-4c4f-b9b4-d2ba63711c84" />
    

### 3.3.5 POST

- 서버로 데이터를 전송
- 폼 제출, 데이터 처리 요청
- 서버가 리소스 이름과 처리 방식을 결정
    
    <img width="617" height="600" alt="image" src="https://github.com/user-attachments/assets/11182f21-9602-4c6f-ae5e-db01401a795a" />
    

### 3.3.6 TRACE

- 클라이언트가 요청을 할 때 방화벽, 프락시, 게이트웨이 등의 애플리케이션을 통과할 수 있다.
- 이들에게는 원래의 HTTP 요청을 수정할 수 있는 기회가 있다.
- TRACE 메서드는 클라이언트에게 자신의 요청이 서버에 도달했을 때 어떻게 보이게 되는지 알려준다.
- 즉, 요청이 서버까지 어떻게 전달되는지 추적
- 요청 메시지를 그대로 응답으로 반환
- 주로 진단용
- 보안 이슈로 비활성화되는 경우 많음
    
    <img width="618" height="357" alt="image" src="https://github.com/user-attachments/assets/4334263b-34ee-4603-bd2d-740da873acdb" />
    

### 3.3.7 OPTIONS

- 서버 또는 리소스가 지원하는 메서드 질의
- Allow 헤더로 응답
- 사전 검사 용도
    
    <img width="616" height="277" alt="image" src="https://github.com/user-attachments/assets/234c7827-61c8-48eb-82e2-84c7e4d04dd1" />
    

### 3.3.8 DELETE

- 리소스 삭제 요청
- 서버 구현에 따라 실제 삭제가 보장되지는 않는다.
    
    <img width="618" height="289" alt="image" src="https://github.com/user-attachments/assets/336f1dae-e7e5-4c9a-b4d5-3b3eef0a265b" />
    

### 3.3.9 확장 메서드

- HTTP는 확장 가능하도록 설계되었다.
- 확장 메서드는 HTTP/1.1 명세에 정의되지 않은 메서드다.
- 표준에 없는 메서드도 사용 가능
- 따라서 프락시는 모르는 메서드를 그대로 전달해야 한다.

## 3.4 상태 코드

### 3.4.1 100-199 정보성 상태 코드

- 클라이언트의 100 continue
    - 클라이언트가 요청 본문을 보내기 전에, 서버가 받을 수 있는 상태인지 확인하기 위한 의도로 도입되었다.
    - 요청에 엔터티가 없다면 클라이언트는 `Expect: 100-continue`값을 보내지 말아야한다.
    - 이 값을 받은 서버는 엔터티를 보낼 것으로 예상하기 때문이다.
    - 또한 서버에서 응답이 오기까지 막연히 기다리지 않고, 약간의 타임아웃 후에 엔터티를 보내야한다.
- 서버의 100 continue
    - 클라이언트에서 `Expect: 100-continue` 값을 받는다면, 서버는 에러코드 혹은 100 continue 응답을 보내야한다.
    - 만약 응답을 보내기 전에 엔터티를 받는 경우 응답하지 않고 요청을 처리한 다음 요청에 대한 결과를 응답해야한다.
- 프락시 서버의 100 continue
서버와 클라이언트의 HTTP 버전에 따라 헤더를 조정한다.

### 3.4.2 200-299 성공 상태 코드

- 요청이 정상 처리됨

| **상태코드** | **사유 구절** | **의미** |
| --- | --- | --- |
| 200 | OK | 엔터티 본문이 요청된 리소스를 갖고 있다. |
| 201 | Created | 서버에 개체를 생성했다. ex) put |
| 202 | Accepted | 요청은 받았으나 결과는 보장되지 않는 상태 |
| 203 | Non-Authoritative Information | 프락시에서 리소스의 사본이 리턴된 상태 |
| 204 | No Content | 서버에서 정상적인 변경 또는 삭제 처리가 이루어진 상태이며 response가 없는 상태 |
| 205 | Reset Content | 현재 페이지에 있는 HTML 폼에 채워진 모든 값을 비우라고 말한다. |
| 206 | Partial Content | 부분 혹은 범위 요청이 성공한 상태 |

### 3.4.3 300-399 리다이렉션 상태 코드

- 리소스 위치가 변경되었거나 다른 위치 사용 권장
- 선택적으로 Location 헤더 사용

| **상태코드** | **사유 구절** | **의미** |
| --- | --- | --- |
| 300 | Multiple Choices | 클라이언트가 동시에 여러 리소스를 가리키는 URL을 요청한 경우, 그 리소스의 목록과 함께 반환한다. |
| 301 | Moved Permanently | 요청한 URL이 옮겨졌을 때 사용한다. 응답은 Location 헤더에 현재 리소스가 존재하고 있는 URL을 포함해야 한다. 브라우저는 이 페이지로 리다이렉트한다. |
| 302 | Found | Location 헤더로 주어진 URL이 임시적일 때 사용한다. |
| 303 | See Other | PUT, POST의 결과로 전송되는 경우가 많다. 리다이렉션이 요청한 리소스 자체에 연결되지 않고 다른 페이지(확인페이지, 진행 페이지 등)으로 연결될 때 사용된다. |
| 304 | Not Modified | 클라이언트가 조건부 조회 요청을 했고, 그 리소스가 최근에 수정된 일이 없다면 재전송할 필요가 없음을 나타낸다. 캐시된 자원으로의 암묵적인 리디렉션이다. |
| 305 | Use Proxy | 리소스가 반드시 프락시를 통해서 접근되어야 함을 나타내기 위해 사용한다. |
| 307 | Temporary Redirect | 요청한 URL이 임시로 옮겨졌을 때 사용한다. 이후에는 원래 URL을 사용한다. |

### 3.4.4 400-499 클라이언트 에러 상태 코드

- 클라이언트의 요청에 문제가 있음

| **상태코드** | **사유 구절** | **의미** |
| --- | --- | --- |
| 400 | Bad Request | 클라이언트가 잘못된 요청을 보냈다고 말해준다. |
| 401 | Unauthorized | 클라이언트 인증이 필요한 상태이다. |
| 403 | Forbidden | 서버에 의해 요청이 거절된 상태이다. |
| 404 | Not Found | 요청한 URL을 찾을 수 없는 상태이다. |
| 405 | Method Not Allowed | 요청한 URL에 대해, 지원하지 않는 메소드로 요청받았을 때 사용한다. 서버는 지원하는 메소드를 allow 헤더에 보내야한다. |
| 407 | Proxy Authentication Required | 리소스에 대해 인증을 요구하는 프락시 서버를 위해 사용한다. |
| 408 | Request Timeout | 클라이언트의 요청을 완수하기에 시간이 너무 많이 걸리는 경우, 서버는 이 상태 코드로 응답하고 연결을 끊을 수 있다. |
| 409 | Conflict | 요청이 충돌을 일으킬 염려가 있다고 생각될 때 이 요청을 보낼 수 있다. |
| 410 | Gone | 리소스가 존재했다가 사라진 경우 클라이언트에게 알려주고자 사용된다. |
| 411 | Length Required | Content-Length 헤더가 필요할 때 사용된다. |
| 412 | Precondition Failed | 클라이언트가 보낸 조건부 조회 요청(Expect 헤더)에 대해 실패한 경우 사용된다. |
| 413 | Request Entity Too Large | 서버가 처리할 수 있는 크기를 초과하는 요청이 들어온 경우 사용된다. |
| 414 | Request URI Too Long | URL의 길이가 너무 길 때 사용된다. |
| 415 | Unsupported Media Type | 서버가 이해하거나 지원하지 못하는 내용 유형의 엔터티를 클라이언트가 보냈을 때 사용한다. |
| 416 | Requested Range Not Satisfiable | 요청 메시지가 리소스의 특정 범위를 요청했는데, 그 범위가 잘못되었 거나 맞지 않을 때 사용한다. |
| 417 | Expectation Failed | Expect 요청 헤더에 서버가 지원하지 않는 값이 있을 때 사용된다. |

### 3.4.5 500-599 서버 에러 상태 코드

- 서버 내부 오류

| **상태코드** | **사유 구절** | **의미** |
| --- | --- | --- |
| 500 | Internal Server Error | 서버가 요청을 처리할 수 없게 만드는 에러를 만났을 때 사용한다. |
| 501 | Not Implemented | 서버가 요청 메소드를 이해하지 못하거나 어떤 리소스를 지원하지 않은 경우에 사용한다. |
| 502 | Bad Gateway | 업스트림 서버로부터 유효하지 않은 응답을 받았을 때 사용된다. |
| 503 | Service Unavailable | 서버가 요청을 처리해 줄 수 없지만 나중에는 가능함을 의미한다. |
| 504 | Gateway Timeout | 다른 서버에게 요청을 보내고 응답을 기다리다 타임아웃이 발생한 경우에 사용된다. |
| 505 | HTTP Version Not Supported | 서버가 지원할 수 없거나 지원하지 않으려고 하는 버전의 프로토콜로된 요청을 받았을 때 사용한다. |

## 3.5 헤더

### 3.5.1 일반 헤더

- 일반 헤더는 메시지 종류에 상관 없이 유용한 정보를 제공한다.
    
    <img width="886" height="464" alt="image" src="https://github.com/user-attachments/assets/2d2063a1-8230-4163-b581-0831a0f3ec3a" />
    

### 3.5.2 요청 헤더

- 클라이언트 정보 전달
    
    <img width="868" height="616" alt="image" src="https://github.com/user-attachments/assets/bda58ea6-226d-452b-86f4-b42ddb971b99" />
    
- **Accept 관련 헤더**
    - 클라이언트는 서버에게 Accept 헤더를 이용해 자신의 선호와 능력을 알려줄 수 있다.
        
        <img width="874" height="340" alt="image" src="https://github.com/user-attachments/assets/d6e1bbe9-0765-4fd2-a36a-728a179f9553" />
        
- **조건부 요청 헤더**
    - 클라이언트는 요청에 몇몇 제약을 넣을 수 있다.
    - 예를 들어 이미 사본을 들고 있다면, 변경되었을 때만 전송해달라고 요청할 수 있다.
        
        <img width="882" height="448" alt="image" src="https://github.com/user-attachments/assets/4d5e0ab5-4a9b-488b-93e0-3c4caf2edb6c" />
        
- **요청 보안 헤더**
    - HTTP는 자체적으로 요청을 위한 간단한 인증요구/응답 체계를 가지고 있다.
        
        <img width="882" height="320" alt="image" src="https://github.com/user-attachments/assets/b28c2a98-d65e-4e5e-8784-4aae22a6ec10" />
        
- **프락시 요청 헤더**
    - 프락시의 기능을 돕기 위한 헤더
        
        <img width="878" height="292" alt="image" src="https://github.com/user-attachments/assets/298079ee-1758-4070-b4a8-35da131c9eac" />
        

### 3.5.3 응답 헤더

- 응답 헤더는 클라이언트에게 부가 정보를 제공한다.
    
    <img width="876" height="454" alt="image" src="https://github.com/user-attachments/assets/53597fcd-f1ec-465c-9e08-81bbe2e0765a" />
    
- **협상 헤더**
    - 서버와 클라이언트가 어떤 표현을 택할 것인가에 대한 협상을 할 수 있도록 지원한다.
        
        <img width="868" height="252" alt="image" src="https://github.com/user-attachments/assets/cadd3fc8-67ff-4ff7-b996-13bba0d575b3" />
        
- **응답 보안 헤더**
    
    <img width="882" height="362" alt="image" src="https://github.com/user-attachments/assets/9bb45cc2-5c9b-4059-b766-eac40571181e" />
    

### 3.5.4 엔티티 헤더

- 일반적으로 엔터티 헤더는 수신자에게 자신이 다루고 있는 것이 무엇인지 말해준다.
    
    <img width="874" height="238" alt="image" src="https://github.com/user-attachments/assets/cef1a26e-2a2e-4530-9be6-db562fe40a7a" />
    
- **콘텐츠 헤더**
    - 콘텐츠 헤더는 콘텐츠에 대한 구체적인 정보를 제공한다.
        
        <img width="880" height="466" alt="image" src="https://github.com/user-attachments/assets/24bca54a-34e6-409d-a588-ecea38224d21" />
        
- **엔터티 캐싱 헤더**
    - 리소스에 대해 캐시된 사본이 아직 유효한지, 언제부터 유효하지 않게 되는지와 같은 정보를 제공한다.
        
        <img width="876" height="266" alt="image" src="https://github.com/user-attachments/assets/a9ba359a-311c-44a3-ad21-8192d736e4e2" />
        

## 3.6 추가 정보

- HTTP/1.1 명세
    - RFC 2616
- W3C HTTP 관련 문서 참고
