# DanggunMarket 🥕  
> 결제 시스템이 존재하는 중고 거래 사이트

- Repository: https://github.com/jgm0327/danggunMarket  
- Branch: `develop`  
- Base project: forked from f-lab-edu/danggunMarket

---

## 1) 프로젝트 소개

**DanggunMarket**는 “중고거래” 도메인에 **결제(거래대금 처리)** 흐름을 포함해 구현한 백엔드 중심 프로젝트입니다.  
대규모 트래픽을 가정하고, 조회/결제/동시성 구간의 병목을 줄이기 위한 구조와 성능 개선을 목표로 했습니다.

> ✅ 한 줄 요약(추천)  
> “중고거래 + 결제 + 트래픽/동시성까지 고려한 백엔드 프로젝트”

---

## 2) 핵심 목표 (Goals)

- 중고거래 핵심 유스케이스(등록 → 탐색/조회 → 거래 → 결제/정산) 구현
- 결제/주문 흐름에서의 **정합성/동시성** 고려
- 성능 병목(특히 조회 트래픽)을 측정하고 개선
- 운영 관점(로깅/모니터링/배포 자동화)을 고려한 구성

---

## 3) 주요 기능 (Features)

> 아래는 “README에 흔히 기대되는 구성”이야.  
> 실제 구현된 것만 ✅로 바꾸고, 미구현은 삭제/추가해줘.

### 회원/인증
- [X] 회원가입 / 로그인
- [X] 토큰 기반 인증 (JWT 등)
- [X] 권한(판매자/구매자) 또는 역할 개념

### 상품/거래
- [X] 상품 등록/수정/삭제
- [X] 상품 목록 조회(정렬/필터/검색)
- [X] 상세 조회
- [ ] 관심(찜) / 조회수 / 신고

### 결제/거래대금
- [ ] 결제 생성/승인/취소
- [ ] 거래 상태 전이(예: CREATED → PAID → COMPLETED/CANCELED)
- [ ] 중복 결제 방지(멱등 처리)
- [ ] (선택) 에스크로/정산 개념

---

## 4) 기술 스택 (Tech Stack)

- Language: Java
- Framework: Spring Boot
- Build: Gradle
- DB: MySQL
- Cache: Caffeine
- Auth: Spring Security + JWT
- Test: JUnit5 / Mockito / Testcontainers (TODO)
- CI/CD: GitHub Actions / Jenkins (TODO)
- Infra: Docker / Docker Compose (TODO)
- Observability: Prometheus / Grafana / Loki (TODO)

---

## 5) 아키텍처 (Architecture)

- API Server
- DB
- Cache (optional)
- (optional) Message broker / Scheduler

```text
[Client] → [API Server] → [DB]
                └→ [Cache] (optional)
