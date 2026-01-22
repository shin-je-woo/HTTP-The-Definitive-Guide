# 02. URL과 리소스

## 2.1 인터넷의 리소스 탐색하기

- URL은 브라우저와 애플리케이션이 리소스를 찾기 위한 주소다.
- 사용자는 URL을 입력하지만 실제로는 애플리케이션이 적절한 프로토콜을 선택해 요청을 보낸다.
- URI는 더 일반적인 개념이며 URL과 URN을 포함한다.
- HTTP에서는 URI라는 용어를 쓰지만 실제 사용은 대부분 URL이다.
    
    <img width="618" height="262" alt="image" src="https://github.com/user-attachments/assets/0b35a675-71c8-49f1-867b-1ed94897df1c" />
    

### 2.1.1 URL이 있기 전 암흑의 시대

- URL 이전에는 각 애플리케이션마다 접근 방식이 달랐다.
- 사용자는 서비스마다 다른 도구와 방법을 배워야 했다.
- URL은 이런 복잡함을 하나의 통일된 인터페이스로 해결했다.

## 2.2 URL 문법

- URL은 리소스를 일관된 방식으로 식별하기 위한 규칙이다.
- 대부분의 URL은 공통된 문법 구조를 따른다.
- 모든 컴포넌트를 항상 포함하지는 않는다.
    
    <img width="512" height="45" alt="image" src="https://github.com/user-attachments/assets/88362340-53a4-43ad-9045-ce7f473f95be" />
    
    <img width="625" height="571" alt="image" src="https://github.com/user-attachments/assets/cb9080bc-d365-47fe-93ba-b88e7d792ba2" />
    

### 2.2.1 스킴: 사용할 프로토콜

- 스킴은 URL의 첫 부분이다.
- 스킴은 리소스에 접근할 때 사용할 프로토콜을 나타낸다.
- 애플리케이션은 스킴을 보고 어떤 통신 방식을 사용할지 결정한다.
- http 스킴은 HTTP 프로토콜을 사용한다는 의미다.
- ftp 스킴은 FTP 프로토콜을 사용해 파일을 전송한다는 의미다.

### 2.2.2 호스트와 포트

- 호스트는 리소스를 제공하는 서버의 이름이나 IP 주소다.
- 포트는 서버 내부에서 리소스를 제공하는 네트워크 창구다.
- URL의 호스트와 포트는 서버의 위치를 결정한다.
- 포트가 생략되면 스킴의 기본 포트를 사용한다.
- HTTP의 기본 포트는 80이다.

### 2.2.3 사용자 이름과 비밀번호

- URL에는 사용자 이름과 비밀번호를 포함할 수 있다.
- 주로 FTP 같은 프로토콜에서 사용된다.
- HTTP URL에서는 보안 문제로 거의 사용되지 않는다.
- 사용자 정보가 없으면 기본 사용자 이름이 사용되기도 한다.

### 2.2.4 경로

- 경로는 서버 내부에서 리소스의 위치를 나타낸다.
- 유닉스 파일 시스템 경로와 유사한 계층 구조를 가진다.
- 슬래시를 기준으로 여러 경로 조각으로 나뉜다.
- 서버는 경로를 해석해 요청된 리소스를 찾는다.

### 2.2.5 파라미터

- 파라미터는 서버에 추가 정보를 전달하기 위해 사용된다.
- 이름과 값의 쌍으로 구성된다.
- 경로 조각마다 개별 파라미터를 가질 수 있다.
- 서버 애플리케이션이 요청을 정확히 처리하도록 돕는다.

### 2.2.6 질의 문자열

- 질의 문자열은 리소스 조회 조건을 전달하기 위해 사용된다.
- 물음표 뒤에 위치한다.
- 이름과 값 쌍의 목록으로 구성된다.
- 데이터베이스 조회나 검색 요청에 자주 사용된다.
    
    <img width="615" height="262" alt="image" src="https://github.com/user-attachments/assets/f6a6d167-d09f-477a-af0d-f5fd29b7f261" />
    

### 2.2.7 프래그먼트

- 프래그먼트는 리소스 내부의 특정 부분을 가리킨다.
- 서버로 전달되지 않고 클라이언트에서만 사용된다.
- HTML 문서의 특정 위치로 이동하는 데 사용된다.
    
    <img width="618" height="462" alt="image" src="https://github.com/user-attachments/assets/de4b36db-dec2-4ee6-872c-8edf3d8b995d" />
    

## 2.3 단축 URL

### 2.3.1 상대 URL

- 상대 URL은 기준 URL을 바탕으로 해석된다.
- 문서 이동이나 구조 변경에 유리하다.
- HTML 문서 안에서 자주 사용된다.
    - 예) <a href=”./hammers.html”>
- 기저 URL을 기준으로 절대 URL로 변환된다.
    
    <img width="615" height="191" alt="image" src="https://github.com/user-attachments/assets/674ed295-7cf8-44bb-b8c1-e574d5c03a8e" />
    

### 2.3.2 URL 확장

- 브라우저는 사용자의 입력을 바탕으로 URL을 자동 완성한다.
- 호스트명 확장과 히스토리 확장이 있다.
- 호스트명 확장
    - 브라우저에 yahoo 입력 → [www.yahoo.com](http://www.yahoo.com) 을 만든다.
- 히스토리 확장
    - 과거에 사용자가 방문했던 URL의 기록을 저장해 놓는다.
    - [http://joes](http://joes-)- 입력 → http://www.joes-hardware.com
- 편의성을 높이지만 프락시 환경에서는 문제를 일으킬 수 있다.

## 2.4 안전하지 않은 문자

### 2.4.1 URL 문자 집합

- URL은 기본적으로 US ASCII 문자 집합을 사용한다.
- 모든 언어의 문자를 직접 표현할 수 없다.
- URL 설계자들은 이런 경우를 대비해 이스케이프 문자를 설계했다.

### 2.4.2 인코딩 체계

- 안전하지 않은 문자는 퍼센트(%) 인코딩으로 변환된다.
- 퍼센트 기호 뒤에 16진수로 ASCII 값을 표현한다.
    
    <img width="610" height="173" alt="image" src="https://github.com/user-attachments/assets/a70d8799-0c99-4dbc-b012-486bcf334152" />
    

### 2.4.3 문자 제한

- 일부 문자는 URL에서 특별한 의미를 가진다.
- 경로 구분자, 질의 구분자 등은 용도가 예약되어 있다.
    
    <img width="632" height="430" alt="image" src="https://github.com/user-attachments/assets/6443c1ed-75f9-42f8-a480-5bed9c75aa32" />
    

### 2.4.4 좀 더 알아보기

- 애플리케이션은 URL을 전송하기 전에 인코딩을 책임져야 한다.
- 안전하지 않은 문자를 인코딩하지 않고 그대로 사용하는 것은 오류의 원인이 된다.
- 모든 문자를 인코딩하는 방식은 권장되지 않지만, 이미 안전한 것으로 판단되는 문자를 재차 인코딩하는 것보다 더 완벽하고 빠른 규칙은 없다.

## 2.5 스킴의 바다

- 스킴은 리소스에 접근하는 방법을 정의한다.
- http와 https가 가장 대표적이다.
- ftp, mailto, file, news, telnet 같은 스킴도 존재한다.

## 2.6 미래

- URL은 위치 기반 식별자라는 한계를 가진다.
- 리소스가 이동하면 URL은 깨질 수 있다.
- URN은 위치와 무관한 식별자를 제공하려는 시도다.
- 지속 통합 자원 지시자(Persistent Uniform Resource Locators, PURL)를 사용하면 URL로 URN의 기능을 제공할 수 있다. 리소스 위치 중개서버를 두고 리소스를 우회적으로 제공한다.
    
    <img width="631" height="364" alt="image" src="https://github.com/user-attachments/assets/1b2daacc-0aa4-4088-83c1-80559f8672b1" />
    
- 단기간에 URL이 사라지지는 않겠지만 보완 기술은 계속 등장할 것이다.

### 2.7 추가 정보

- URI와 URL 표준은 W3C와 IETF 문서를 참고한다.
- RFC 2396, RFC 2141, RFC 1808 등이 주요 문서다.
