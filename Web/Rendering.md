### 전체적인 과정
1. URL 입력
2. DNS 조회를 통해 IP 주소 획득
3. TCP/TLS Handshake -> 연결
4. HTTP 요청 -> HTML 받기
5. HTML 파싱 -> DOM 트리
6. CSS 파싱 -> CSSOM 트리
7. DOM + CSSOM -> 렌더 트리
8. 레이아웃 -> 위치/크기 계산
9. 페인트 -> 픽셀 그리기
10. 합성 -> 화면 표시

<br>

### 1️⃣ 네트워크 - 서버에서 데이터 가져오기
- URL 입력 및 DNS 조회
- TCP 연결 및 HTTP 요청
  - 브라우저 -> 서버: TCP 3-way Handshake
  - 브라우저 -> 서버: HTTPS면 TLS Handshake
  - 브라우저 -> 서버: GET/HTTP/1.1 (HTML 요청)
- 서버 응답
  - 서버 -> 브라우저: HTML 파일 전송
  - 서버 -> 브라우저: 이 HTML에 CSS, JS, 이미지도 필요해~

<br>

### 2️⃣ 렌더링 - 화면에 그리기
- HTML 파싱 -> DOM(Document Object Model) 트리 생성
  - DOM(Document Object Model)은 HTML을 자바스크립트가 이해할 수 있는 객체 트리 구조로 변환한 것이다.
- CSS 파싱 -> CSSOM(CSS Object Model) 트리 생성
  - CSSOM(CSS Object Model)은 CSS를 트리 구조로 변환한 것
- DOM + CSSOM -> 렌더 트리 생성
  - display:none인 요소는 렌더 트리에서 제외한다.
  - `<head>`, `<script>` 같은 보이지 않는 요소도 제외한다.
  - 즉, 렌더 트리는 실제로 화면에 보일 요소만 포함한다.
- 레이아웃(Layout) / 리플로우(Reflow)
  - 렌더 트리를 순회하면서 각 요소의 정확한 위치와 크기를 계산한다.
  - 뷰포트(브라우저 창) 크기를 기준으로 각 요소의 위치, 크기를 계산하는 단계다.
- 페인트(Paint)
  - 레이아웃 정보를 바탕으로 텍스트 그리기, 색상 채우기, 이미지 그리기, 그림자/테두리 그리기
  - 픽셀로 변환
    - 계산된 위치에 실제 픽셀을 그리는 단계
    - 아직 화면에는 안 보인다.
- 합성(Composite)
  - 여러 레이어(배경 레이어, 텍스트 레이어, 이미지 레이어)를 합쳐서 최종 화면 만들기
  - GPU가 합성해서 화면에 표시한다.
  - 여러 레이어를 합쳐서 최종 화면을 만들고 GPU로 전송하면 화면에 보인다.
