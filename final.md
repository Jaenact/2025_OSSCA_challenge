# 2025 오픈소스 컨트리뷰션 아카데미 - 기여 활동 포트폴리오

본 리포지토리는 '2025 오픈소스 컨트리뷰션 아카데미' 프로그램의 멘티로 참여하며 Project Discovery의 `nuclei-templates` 오픈소스 프로젝트에 기여한 내역을 정리한 포트폴리오입니다.

## 📌 활동 요약 (Executive Summary)

약 13주간 Project Discovery의 **Nuclei-Templates** 프로젝트에 기여하며 웹 애플리케이션의 취약점 탐지 스펙트럼을 확장하고, 템플릿의 전반적인 품질과 신뢰도를 향상하는 데 집중했습니다.

주요 기여 활동은 다음과 같습니다:

  * **신규 취약점 템플릿 개발:** CVE-2023-27163 (SSRF), CVE-2025-1302 (RCE)  등 알려진 CVE의 탐지 룰을 개발했습니다.
  * **DAST/퍼징 템플릿 개발:** 제로데이 위협에 대응하기 위한 범용 퍼징 템플릿을 개발했습니다.
      * OS Command Injection (Unix/Windows)을 위한 출력/시간 기반 이중 검증 로직을 설계했습니다.
      * GraphQL 설정 오류(인트로스펙션, UI 노출)를 탐지하는 통합 템플릿을 개발했습니다.
  * **핵심 템플릿 유지보수 및 개선:**
      * **CSP Bypass:** 최신 우회 로직을 다수 추가하고 , 패치되어 더 이상 동작하지 않는 19개의 템플릿을 제거했습니다. 또한, 외부 서비스 API 변경에 따른 페이로드 수정(HTTP→HTTPS, 파라미터 변경)을 진행했습니다.
      * **Time-Based SQLi:** 다중 DBMS (MySQL, PostgreSQL, SQL Server)를 지원하도록 페이로드를 대폭 확장하고, 서버 부하를 유발하는 `BENCHMARK` 등 위험 함수를 제거하여 안정성을 확보했습니다.
  * **커뮤니티 및 문서화:**
      * `CONTRIBUTING.md`의 깨진 링크를 수정했습니다.
      * `README_KR.md`의 통계 정보를 최신화하고, 한국어 번역을 자연스럽게 개선했습니다.

## 📈 정량적 성과 (Quantitative Achievements)

아카데미 기간 동안의 기여 활동을 요약한 정량적 성과입니다.

**기여 요약 (Contribution Summary)**
| 항목 | 총 합계 |
| :--- | :--- |
| Pull Request | 18 |
| Merge | 10 |
| Commit | 28 |

**코드 변경량 (Code Change Volume)**
| 항목 | 라인 수 |
| :--- | :--- |
| 추가된 라인 (Added) | 1,157 |
| 삭제된 라인 (Deleted) | 1,067 |
*(참고: 19개의 오래된 템플릿을 제거하는 유지보수 작업을 포함하여 삭제된 라인 수가 높게 집계되었습니다 ).*

## ✅ 병합된 Pull Request 목록 (Merged Pull Requests)

실제로 `projectdiscovery/nuclei-templates` 메인 브랜치에 병합된 기여 내역입니다.

| PR \# | 제목 | 기여 유형 |
| :--- | :--- | :--- |
| **[\#12723](https://www.google.com/search?q=https://github.com/projectdiscovery/nuclei-templates/pull/12723)** | `add CVE-2023-27163 template`  | 신규 템플릿 (CVE) |
| **[\#12791](https://www.google.com/search?q=https://github.com/projectdiscovery/nuclei-templates/pull/12791)** | `feat(sqli): Add multiple payloads and author to time-based-sqli template`  | 유지보수 (개선) |
| **[\#13062](https://www.google.com/search?q=https://github.com/projectdiscovery/nuclei-templates/pull/13062)** | `chore(csp-bypass): Remove patched or non-working endpoints`  | 유지보수 (제거) |
| **[\#13064](https://www.google.com/search?q=https://github.com/projectdiscovery/nuclei-templates/pull/13064)** | `fix(csp-bypass): Correct protocols and payloads for several endpoints`  | 유지보수 (수정) |
| **[\#13068](https://www.google.com/search?q=https://github.com/projectdiscovery/nuclei-templates/pull/13068)** | `feat(templates): Add Nuclei template for Typekit CSP bypass`  | 신규 템플릿 (CSP) |
| **[\#13074](https://github.com/projectdiscovery/nuclei-templates/pull/13074)** | `feat(templates): Add Nuclei template for clients6 CSP bypass` | 신규 템플릿 (CSP) |
| **[\#13115](https://www.google.com/search?q=https://github.com/projectdiscovery/nuclei-templates/pull/13115)** | `feat(template): add Salesforce CSP bypass detection` | 신규 템플릿 (CSP) |
| **[\#13117](https://github.com/projectdiscovery/nuclei-templates/pull/13117)** | `feat(template): add Beslist.nl CSP bypass detection` | 신규 템플릿 (CSP) |
| **[\#13249](https://www.google.com/search?q=https://github.com/projectdiscovery/nuclei-templates/pull/13249)** | `feat: Updated README_KR`  | 문서화 (수정) |
| **[\#13405](https://www.google.com/search?q=https://github.com/projectdiscovery/nuclei-templates/pull/13405)** | `docs: Fix broken links in contribution guide` | 문서화 (수정) |

## 🛠️ 주요 기여 상세 내역 (Detailed Contributions)

### 1\. 신규 취약점 템플릿 개발 (CVE & DAST)

  * **CVE-2023-27163 (SSRF)** 
      * **내용:** Request-Baskets의 Blind SSRF 취약점 탐지.
      * **설계:** OAST(Out-of-Band) 콜백을 통해 서버의 응답 없이도 취약점을 확인하는 로직 구현.
  * **CVE-2025-1302 (RCE)**
      * **내용:** `jsonpath-plus` 라이브러리의 `eval()` 함수 관련 RCE 취약점 탐지.
      * **설계:** 시스템에 영향을 주지 않는 `console.log("nuclei-safe")` 페이로드를 사용하여 안전하게 `eval()` 실행 여부만 검증.
  * **OS Command Injection (Unix/Windows)** 
      * **목표:** 제로데이 탐지를 위한 범용 퍼징(Fuzzing) 템플릿 개발.
      * **설계:** 이중 검증 로직 채택.
        1.  **출력 기반 (Output-based):** `dir`, `id` 등의 비파괴적 명령어 실행 결과를 응답 본문에서 확인.
        2.  **시간 기반 (Time-based):** `sleep 5`, `ping -n 5` 등을 주입하여 응답 지연(4초 이상)으로 Blind 취약점 탐지.
  * **GraphQL 설정 오류** 
      * **목표:** 인트로스펙션(Introspection) 활성화 및 개발자용 UI(GraphiQL) 노출을 단일 템플릿으로 통합 탐지.
      * **설계:** `application/json`, `application/graphql` 등 다양한 Content-Type을 테스트하고 , 응답 본문에 `_schema`와 `types` 키워드가 모두 존재하는지 AND 조건으로 엄격하게 검증하여 오탐 최소화.

### 2\. CSP Bypass 템플릿 개발 및 유지보수

느슨한 CSP 정책과 HTML Injection이 결합될 때 발생하는 XSS를 탐지하는 템플릿을 집중적으로 개발하고 유지보수했습니다.

  * **신규 템플릿 (4건):**

      * `Salesforce` (omtr2.partners.salesforce.com) 
      * `Beslist.nl` (ct.beslist.nl) 
      * `Typekit` (typekit.com / JSONP) 
      * `Google` (clients6.google.com / JSONP) 

  * **핵심 설계 (2단계 하이브리드 탐지):**

      * **1단계 (HTTP Pre-check):** `Content-Security-Policy` 헤더에 신뢰 도메인(예: `salesforce.com`)이 있는지 가볍게 확인.
      * **2단계 (Headless Validation):** 1단계를 통과하면, Headless 브라우저를 실행하여 실제 공격 페이로드를 주입하고 `alert()` 창이 뜨는지(`waitdialog` 액션) 검증하여 취약점을 확증.

  * **템플릿 유지보수 (3건):**

      * **패치된 템플릿 제거 (19개):** 원천 소스(renniepak/CSPBypass)에서 패치가 확인된 19개의 템플릿을 제거하여 프로젝트의 정확성과 스캔 효율성 증대[.
      * **프로토콜/페이로드 수정:** `http://`를 `https://`로 수정(Mixed Content 차단 우회)하고, 불안정한 JSONP 페이로드 구문을 교정.
      * **API 변경 대응:** `www.google.com` 엔드포인트의 파라미터가 `callback`에서 `jsonp`로 변경된 사항을 신속히 반영하여 템플릿 기능 복원.

### 3\. 핵심 템플릿 개선 (Time-Based SQLi)

  * **기존 문제:** `time-based-sqli` 템플릿이 MySQL에 편중되어 있고, `BENCHMARK` 등 서버 부하를 유발하는 위험한 함수를 사용.
  * **개선 내역:**
    1.  **다중 DBMS 지원:** MySQL, PostgreSQL (`pg_sleep`), SQL Server (`WAITFOR DELAY`) 등 주요 DB별 시간 기반 페이로드를 대거 추가.
    2.  **안전성 강화:** `BENCHMARK`, `RANDOMBLOB` 등 서비스 거부(DoS) 위험이 있는 함수를 전면 제거하여 운영 환경에서 안전하게 사용하도록 개선.

### 4\. 문서화 및 커뮤니티

  * **CONTRIBUTING.md 수정:** 깨진 가이드라인 링크를 수정하고, 외부 링크를 저장소 내 상대 경로로 변경하여 버전 일관성 확보.
  * **README\_KR.md 최신화:**
      * **현지화:** 어색한 번역 투의 문장을 원어민에게 자연스러운 표현으로 수정.
      * **통계 갱신:** 전체 템플릿 수 (4,012 → 11,344), CVE (1,325 → 3,288) 등 최신 통계로 갱신하여 프로젝트의 현재 규모를 정확히 반영.

## 🏃‍♂️ 아카데미 활동 내역 (Program Activities)

  * 2025 오픈소스 컨트리뷰션 아카데미 발대식 참여
  * 온/오프라인 정기 팀 회의 진행 (매주 수요일 등)
  * 오프라인 '모각코' (모여서 각자 코딩) 세션 참여
