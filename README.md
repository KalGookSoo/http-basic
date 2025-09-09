# http-basic
HTTP 기초

## 목차

### Chapter 01 인터넷 네트워크

#### [01-1 인터넷 통신](chapters/01-1-인터넷-통신.md)
- 인터넷이 동작하는 원리와 패킷 교환 방식
- 클라이언트-서버 간 요청/응답 개념
- 네트워크 계층과 OSI 7계층의 개요

#### [01-2 IP(인터넷 프로토콜)]()
- IP 주소의 구조(IPv4/IPv6)
- 라우팅과 서브네팅의 기초 개념
- IP 패킷의 구성 요소(헤더, 페이로드)

#### [01-3 TCP, UDP]()
- TCP의 연결지향, 신뢰성, 흐름/혼잡 제어
- UDP의 비연결성, 경량성, 실시간성 장점
- 용도 비교: 파일전송/웹(TCP) vs 스트리밍/게임(UDP)

#### [01-4 PORT]()
- 포트의 역할과 범위(Well-known/Registered/Dynamic)
- 소켓(아이피+포트) 개념과 프로세스 매핑
- 서비스 구분을 위한 포트 사용 예시(HTTP 80, HTTPS 443)

#### [01-5 DNS]()
- 도메인 네임을 IP로 변환하는 시스템
- 쿼리 흐름: 로컬 캐시 → 리커시브 → 권한 있는 네임서버
- A/AAAA/CNAME/NS 등 주요 레코드 타입

### Chapter 02 URI와 웹 브라우저 요청 흐름

#### [02-1 URI]()
- URI/URL/URN의 차이
- 스키마, 호스트, 포트, 경로, 쿼리, 프래그먼트 구성
- 인코딩 규칙과 예약 문자

#### [02-2 웹 브라우저 요청 흐름]()
- 주소창 입력부터 응답 렌더링까지의 단계
- DNS 조회, TCP 핸드셰이크, TLS, HTTP 요청/응답 순서
- 브라우저 캐시, 프리로드/프리페치의 영향

### Chapter 03 HTTP 기본

#### [03-1 모든 것이 HTTP]()
- 웹 문서, 이미지, API, 스트리밍 등 전송 단위로서의 HTTP
- HTTP/1.1, HTTP/2, HTTP/3의 간단 비교
- 프로토콜 독립성과 확장성

#### [03-2 클라이언트 서버 구조]()
- 역할 분리: 클라이언트(UI/요청) vs 서버(비즈니스/응답)
- 무상태 통신에서의 확장성과 부하 분산
- 프록시, 게이트웨이, 로드밸런서의 위치

#### [03-3 Stateful, Stateless]()
- 상태 유지 vs 비상태의 차이와 장단점
- 세션/쿠키/토큰을 통한 상태 관리 전략
- 확장성, 장애 복구, 캐시 적합성 관점 비교

#### [03-4 비 연결성(connectionless)]()
- 요청-응답 후 연결을 종료하는 특성
- 연결 재사용(keep-alive)과 HTTP/2 멀티플렉싱
- 연결 비용과 지연 시간에 대한 고려

#### [03-5 HTTP 메시지]()
- 시작줄, 헤더, 바디 구조
- 요청 라인(method, URI, version)과 상태라인(status code)
- 헤더 예시와 바디 포맷(JSON, HTML, Form)

### Chapter 04 HTTP 메서드

#### [04-1 HTTP API를 만들어보자]()
- 리소스 중심 설계: URI는 명사, 행위는 메서드로 구분
- 표준 메서드 활용해 CRUD 매핑하기
- 엔드포인트 버저닝과 문서화 기본

#### [04-2 HTTP 메서드 - GET, POST]()
- GET: 안전(safe), 캐시 가능, 멱등성(idempotent) X
- POST: 리소스 생성/행위 트리거, 바디 전송
- 사용 시나리오와 캐시/브라우저 동작 차이

#### [04-3 HTTP 메서드 - PUT, PATCH, DELETE]()
- PUT: 전체 교체, 멱등적 특성
- PATCH: 부분 변경, 멱등성 보장 아님
- DELETE: 삭제, 멱등적 동작 기대

#### [04-4 HTTP 메서드의 속성]()
- 안전성(Safe), 멱등성(Idempotent), 캐시가능성(Cacheable)
- 조건부 요청과 병행 제어와의 연계
- 부작용과 재시도 전략 고려

### Chapter 05 HTTP 메서드 활용

#### [05-1 클라이언트에서 서버로 데이터 전송]()
- 쿼리 파라미터 vs 메시지 바디의 용도 차이
- 폼 전송(application/x-www-form-urlencoded, multipart)
- JSON 전송과 콘텐츠 타입 지정

#### [05-2 HTTP API 설계 예시]()
- 컬렉션/개별 리소스 URI 패턴
- 계층 관계와 하위 리소스 표현
- 오류 응답 포맷과 상태코드 매핑

### Chapter 06 HTTP 상태코드

#### [06-1 HTTP 상태코드 소개]()
- 1xx/2xx/3xx/4xx/5xx 범주 개요
- 의미 체계와 표준 문서(RFC) 레퍼런스
- 애플리케이션 수준 규약의 필요성

#### [06-2 2xx - 성공]()
- 200 OK, 201 Created, 204 No Content 차이
- 생성 위치 전달(Location 헤더) 관례
- 멱등 요청에서의 응답 처리

#### [06-3 3xx - 리다이렉션1]()
- 301 Moved Permanently, 302 Found 의미
- 303 See Other와 POST-Redirect-GET 패턴
- 304 Not Modified의 캐시 최적화

#### [06-4 3xx - 리다이렉션2]()
- 307 Temporary Redirect, 308 Permanent Redirect
- 메서드 보존 여부와 브라우저 동작 차이
- SEO와 링크 유지 전략

#### [06-5 4xx - 클라이언트 오류, 5xx - 서버 오류]()
- 400/401/403/404 주요 케이스
- 409/412/429 등 상황별 선택 가이드
- 500/502/503/504 서버 장애 대응

### Chapter 07 HTTP 헤더1 - 일반 헤더

#### [07-1 HTTP 헤더 개요]()
- 엔티티/표현/요청/응답 헤더의 분류
- 표준 vs 커스텀 헤더 네이밍 규칙
- 대소문자 비민감성과 전송 형식

#### [07-2 표현]()
- Content-Type, Content-Length, Content-Encoding
- 언어/문자셋: Content-Language, charset
- 표현 메타데이터와 협상 기반

#### [07-3 콘텐츠 협상]()
- Accept, Accept-Language, Accept-Encoding
- 서버 선호도(q 값)와 최적 표현 선택
- Vary 헤더와 캐시 안정성

#### [07-4 전송 방식]()
- 전송 인코딩(chunked)과 지속 연결
- 범위 요청(Range)과 재개 다운로드
- 압축 전송과 성능 최적화

#### [07-5 일반 정보]()
- Date, Server, Via 등 정보성 헤더
- Referrer-Policy, User-Agent 이해
- Retry-After와 재시도 제어

#### [07-6 특별한 정보]()
- Host, Origin, Location의 역할
- ETag/If-Match로 조건부 갱신
- Allow, Content-Location 활용

#### [07-7 인증]()
- WWW-Authenticate, Authorization 동작
- Basic vs Bearer 토큰 흐름
- 인증/인가와 상태관리 연계

#### [07-8 쿠키]()
- Set-Cookie, Cookie 포맷과 속성(Path, Domain, Secure, HttpOnly, SameSite)
- 세션 유지와 추적, 보안 고려사항
- 쿠키와 토큰 기반 인증 비교

### Chapter 08 HTTP 헤더2 - 캐시와 조건부 요청

#### [08-1 캐시 기본 동작]()
- 캐시 적중(hit)/미스(miss) 흐름
- 유효기간과 신선도 지표(age, max-age)
- 개인/공용 캐시 구분

#### [08-2 검증 헤더와 조건부 요청]()
- ETag/If-None-Match 흐름
- Last-Modified/If-Modified-Since 비교
- 조건부 갱신과 대역폭 절감

#### [08-3 캐시와 조건부 요청 헤더]()
- Cache-Control 지시어(no-store, no-cache, max-age, s-maxage)
- Expires, Pragma와의 관계
- Revalidation 전략(강제/약한)

#### [08-4 프록시 캐시]()
- 프록시 캐시와 CDN의 역할
- s-maxage, stale-while-revalidate 등 활용
- 공용 캐시 검증과 무결성

#### [08-5 캐시 무효화]()
- 강제 무효화와 재검증 트리거
- Surrogate-Key/Tag 기반 무효화
- 캐시 파기 정책과 주의점

### [정답 및 해설](answers_and_explanations.md)

