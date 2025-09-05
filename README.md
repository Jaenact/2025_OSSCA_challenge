# Project Discovery 기여 활동 포트폴리오

이 문서는 '오픈소스 컨트리뷰션 2025' 프로그램 참여의 일환으로 **Project Discovery**에 기여한 활동을 정리한 포트폴리오입니다.

## 1. Project Discovery 소개

Project Discovery는 보안 전문가와 개발자를 위한 강력한 오픈소스 도구를 개발하는 조직입니다. 복잡한 보안 작업을 자동화하고 간소화하여 누구나 쉽게 보안을 점검하고 강화할 수 있도록 돕는 것을 목표로 합니다.

주요 프로젝트로는 템플릿 기반의 고속 스캐너인 **Nuclei**가 있으며, 전 세계 수많은 보안 연구원과 기업에서 활발하게 사용되고 있습니다.

## 2. Nuclei Templates 란?

Nuclei는 YAML 형식의 템플릿을 사용하여 수천 가지의 보안 취약점을 신속하게 탐지하는 도구입니다. Nuclei의 핵심은 바로 이 **템플릿**에 있습니다.

템플릿들은 커뮤니티에 의해 지속적으로 추가되고 개선되며, 새로운 취약점이 발견될 때마다 해당 취약점을 탐지할 수 있는 로직을 담고 있습니다. 따라서 템플릿에 기여하는 것은 Nuclei 스캐너의 탐지 능력을 직접적으로 향상시키고, 전 세계 사용자들에게 더 안전한 환경을 제공하는 데 중요한 역할을 합니다.

저는 이 Nuclei 템플릿 리포지토리에 새로운 CVE 및 보안 설정 오류 탐지 템플릿을 추가하고 기존 템플릿을 개선하는 방식으로 기여했습니다.

## 3. 기여한 Pull Request 목록

| 제목 | 링크 | 상태 |
| --- | --- | --- |
| `add CVE-2023-27163 template` | [\#12723](https://github.com/projectdiscovery/nuclei-templates/pull/12723) | Merged |
| `add CVE-2025-1302 detection template` | [\#12724](https://github.com/projectdiscovery/nuclei-templates/pull/12724) | Open |
| `Add Unix and Windows Command Injection Detecti` | [\#12821](https://github.com/projectdiscovery/nuclei-templates/pull/12821) | Open |
| `chore(csp-bypass): Remove patched or non-workin` | [\#255328](https.com/projectdiscovery/nuclei-templates/pull/255328) | Open |
| `feat(graphql): Add template for GraphQL introspecti` | [\#12955](https://github.com/projectdiscovery/nuclei-templates/pull/12955) | Open |
| `feat(sql): Add multiple payloads and author to time-`| [\#354669](https://github.com/projectdiscovery/nuclei-templates/pull/354669) | Merged |
| `feat(templates): Add Nuclei template for client6 CS`| [\#13074](https://github.com/projectdiscovery/nuclei-templates/pull/13074) | Merged |
| `feat(templates): Add Nuclei template for Typekit CS`| [\#772676](https.com/projectdiscovery/nuclei-templates/pull/772676) | Merged |
| `fix(csp-bypass): Correct protocols and payloads for` | [\#097631](https://github.com/projectdiscovery/nuclei-templates/pull/097631) | Merged |


## 4. 주요 기여 내용 및 배운 점

-   **CVE 기반 템플릿 작성:** 최신 CVE(CVE-2023-27163, CVE-2025-1302 등)를 분석하고, 이를 탐지할 수 있는 Nuclei 템플릿을 작성하여 실제 위협에 대응하는 경험을 쌓았습니다.
-   **보안 설정 오류 탐지:** 리눅스 시스템의 잘못된 보안 설정을 탐지하는 템플릿을 추가하여, 공격 표면을 줄이는 방어적 보안 관점의 기여를 진행했습니다.
-   **오픈소스 협업:** GitHub의 PR(Pull Request), 코드 리뷰, 이슈 트래킹 등 오픈소스 생태계의 협업 방식을 직접 경험하며 다른 개발자들과 소통하는 능력을 길렀습니다.
