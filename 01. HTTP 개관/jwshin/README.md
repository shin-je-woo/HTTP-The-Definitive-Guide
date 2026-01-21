# 01. HTTP 개관

## 1.1 HTTP 인터넷의 멀티미디어 배달부

- HTTP는 전 세계 웹에서 데이터를 전달하는 공통 프로토콜이다.
- HTML 문서, 이미지, 동영상, 오디오 등 다양한 멀티미디어 리소스를 전송한다.
- 빠르고 단순하며 신뢰성 있는 전송을 목표로 설계되었다.
- 개발자는 네트워크 세부 구현보다 애플리케이션 기능에 집중할 수 있다.

## 1.2 웹 클라이언트와 서버

- 웹 콘텐츠는 서버에 저장되고 클라이언트가 요청한다.
- 클라이언트는 HTTP 요청을 보내고 서버는 HTTP 응답을 돌려준다.
- 이 요청과 응답 구조가 웹의 기본 동작 방식이다.
- 웹브라우저는 가장 대표적인 HTTP 클라이언트다.
    
    <img width="624" height="217" alt="image" src="https://github.com/user-attachments/assets/4b44dba6-6eb3-4137-b500-7f2bd8d9abb2" />
    

## 1.3 리소스

- 리소스는 웹에서 제공되는 모든 콘텐츠의 원천이다.
- 정적 파일뿐 아니라 요청 시 동적으로 생성되는 데이터도 리소스다.
- 이미지, 문서, 동영상, 프로그램 출력 결과 모두 리소스에 포함된다.
- 웹 서버는 리소스를 관리하고 요청에 따라 제공한다.
    
    <img width="622" height="556" alt="image" src="https://github.com/user-attachments/assets/1652f702-0c54-4498-bd56-39fec1f99a45" />
    

### 1.3.1 미디어 타입

- HTTP는 전송되는 데이터의 형식을 MIME 타입으로 명시한다.
- MIME 타입은 주 타입과 부 타입으로 구성된다.
- 예시로 text/html, image/jpeg, image/gif 등이 있다.
- 클라이언트는 MIME 타입을 기준으로 데이터를 처리한다.
    
    <img width="619" height="283" alt="image" src="https://github.com/user-attachments/assets/7636339a-365f-4578-a96d-9ca3b9dee0d7" />
    

### 1.3.2 URI

- URI: Uniform Resource Identifier
- URI는 리소스를 식별하기 위한 통합된 이름 체계다.
- 인터넷 상의 리소스를 유일하게 가리킨다.
- URL과 URN을 모두 포함하는 상위 개념이다.
- HTTP는 주로 URI를 통해 리소스를 지정한다.
    
    <img width="619" height="308" alt="image" src="https://github.com/user-attachments/assets/acf8f970-d8bf-488d-8118-bd0cb03a67ec" />
    

### 1.3.3 URL

- URL: Uniform Resource Locator
- URL은 리소스의 위치와 접근 방법을 함께 나타낸다.
- 스킴, 호스트, 경로로 구성된다.
    - 스킴 예시: http://
    - 호스트 예시: www.joes-hardware.com
    - 경로 예시: /specials/saw-blade.gif
- 오늘날 대부분의 웹 주소는 URL이다.

### 1.3.4 URN

- URN: Uniform Resource Name
- URN은 위치와 무관하게 리소스를 식별한다.
- 리소스를 여기저기로 옮기더라도 문제없이 동작하는 것이 목적이다.
- 실제 웹에서는 거의 사용되지 않는다.
- 실무에서는 URL이 사실상 표준처럼 사용된다.

## 1.4 트랜잭션

- HTTP 트랜잭션은 요청과 응답 한 쌍으로 구성된다.
- 하나의 웹 페이지를 표시하기 위해 여러 트랜잭션이 발생할 수 있다.
    
    <img width="624" height="318" alt="image" src="https://github.com/user-attachments/assets/a27656ab-882c-4055-a504-a636d7007ed8" />
    

### 1.4.1 메서드

- 메서드는 서버에 어떤 동작을 요청할지 나타낸다.
- 자주 쓰이는 메서드는 GET, PUT, DELETE, POST, HEAD다.

### 1.4.2 상태 코드

- 상태 코드는 요청 처리 결과를 나타낸다.
- 200은 성공, 302는 리다이렉트, 404는 리소스 없음이다.
- 상태 코드는 숫자가 핵심이며 사유 구절은 설명용이다.

### 1.4.3 웹페이지는 여러 객체로 이루어질 수 있다

- 애플리케이션은 보통 하나의 작업을 수행하기 위해 여러 HTTP 트랜잭션을 수행한다.
- 하나의 웹페이지는 여러 리소스로 구성된다.
- HTML 문서, 이미지, 그래픽 조각, 스크립트가 각각 별도 요청으로 처리된다.

## 1.5 메시지

- HTTP 메시지는 단순한 텍스트 기반 구조다.
- 시작줄, 헤더, 본문으로 구성된다.
- 요청 메시지와 응답 메시지 형식은 유사하다.
    
    <img width="620" height="591" alt="image" src="https://github.com/user-attachments/assets/52b4852a-78cf-4073-a7d6-1ef04feeea50" />
    

## 1.6 TCP 커넥션

- HTTP는 TCP 위에서 동작한다.
- TCP는 오류 없는 전송과 순서 보장을 제공한다.
- HTTP는 TCP의 신뢰성을 기반으로 단순성을 유지한다.

### 1.6.1 TCP/IP

- HTTP는 애플리케이션 계층 프로토콜이다.
- HTTP는 네트워크 통신의 핵심적인 세부사항에 대해서 신경 쓰지 않는다.
- 실제 데이터 전송은 TCP/IP가 담당한다.
    
    <img width="623" height="249" alt="image" src="https://github.com/user-attachments/assets/f4cc0cb3-1c97-4fd2-8247-4c146f900a63" />
    

### 1.6.2 접속 IP 주소 그리고 포트번호

- 클라이언트는 서버의 IP 주소와 포트 번호로 연결한다.
- URL에는 호스트명과 포트 정보가 포함될 수 있다.
- 포트가 생략되면 HTTP는 기본적으로 80번을 사용한다.
- DNS는 호스트명을 IP 주소로 변환한다.
    
    <img width="639" height="645" alt="image" src="https://github.com/user-attachments/assets/c70aa3cc-d821-4225-a301-f60409c51ed2" />
    

### 1.6.3 텔넷을 이용한 실제 예제

- HTTP는 텍스트 기반이므로 텔넷으로 직접 요청을 보낼 수 있다.
- 이를 통해 HTTP 메시지 구조를 명확히 이해할 수 있다.

### 1.7 프로토콜 버전

- HTTP는 여러 버전을 거쳐 발전해왔다.
- HTTP 0.9는 매우 단순한 초기 버전이다.
- HTTP 1.0은 헤더와 상태 코드를 도입했다.
- HTTP 1.0+는 비공식 확장을 포함한다.
- HTTP 1.1은 구조적 결함과 성능을 개선했다.
- HTTP 2.0은 성능 개선을 목표로 설계되었다.

## 1.8 웹의 구성요소

- 웹은 여러 HTTP 구성요소로 이루어진다.

### 1.8.1 프락시

- 클라이언트와 서버 사이에서 요청과 응답을 중계한다.
- 보안, 필터링, 성능 개선 목적으로 사용된다.
    
    <img width="621" height="238" alt="image" src="https://github.com/user-attachments/assets/65c9146e-ad1a-43da-a883-bb6675fbaa20" />
    

### 1.8.2 캐시

- 자주 요청되는 리소스를 가까운 곳에 저장한다.
- 응답 속도를 높이고 네트워크 부하를 줄인다.
    
    <img width="615" height="299" alt="image" src="https://github.com/user-attachments/assets/ede811ba-1f2f-4fe8-add6-f92d07758141" />
    

### 1.8.3 게이트웨이

- 서로 다른 프로토콜 간 변환을 담당한다.
- 클라이언트는 이를 일반 서버처럼 인식한다.
    
    <img width="609" height="198" alt="image" src="https://github.com/user-attachments/assets/633bcb02-c14d-4d41-9843-b6cc4889ae32" />
    

### 1.8.4 터널

- 데이터를 그대로 전달하는 중계 방식이다.
- SSL 트래픽 전달에 주로 사용된다.
    
    <img width="611" height="331" alt="image" src="https://github.com/user-attachments/assets/25ed32d4-4a01-43f2-9a4d-e74d0fc4d339" />
    

### 1.8.5 에이전트

- 사용자를 대신해 HTTP 요청을 생성한다.
- 웹브라우저 외에도 검색 엔진 크롤러가 이에 해당한다.
    
    <img width="527" height="467" alt="image" src="https://github.com/user-attachments/assets/189ce3da-cf55-476d-be58-559cac290263" />
    

### 1.9 시작의 끝

- 이 장에서는 HTTP의 전체 그림을 개략적으로 다뤘다.
- 이후 장에서 각 요소를 더 깊이 다룬다.

### 1.10 추가 정보

- HTTP 관련 RFC와 표준 문서를 참고하면 좋다.
- W3C와 IETF 자료를 참고하면 좋다.
