# Nuclei Templates 분석 및 CVE-2024-55416 탐지

## nuclei-template 분석

### git 첫 페이지 모습
<img width="2048" height="986" alt="image" src="https://github.com/user-attachments/assets/fd4c7d84-3fc2-4e01-9310-959398141df5" />

### nuclei-templates 폴더 구조

```
nuclei-templates/
├── .github/                  # GitHub 워크플로, PR 및 이슈 템플릿
├── http/                     # HTTP 기반 취약점 템플릿
│   ├── cves/                 # CVE 기반 취약점 템플릿
│   ├── vulnerabilities/      # 웹 프레임워크 및 라이브러리 취약점
│   ├── misconfiguration/     # 잘못된 설정 감지용 템플릿
│   ├── exposures/            # 민감 정보 노출 (.git, .env 등)
│   ├── technologies/         # 기술 스택 감지용 템플릿
│   ├── fuzzing/              # Fuzzing 기반 탐지 템플릿
│   └── ...                   # 기타 하위 디렉토리
├── dns/                      # DNS 관련 탐지 템플릿
├── ssl/                      # SSL 인증서 및 암호화 이슈 탐지
├── network/                  # TCP/UDP 등 네트워크 계층 취약점
├── workflows/                # 여러 템플릿을 연결하는 흐름 정의
├── file/                     # 파일 시스템 기반 탐지
├── headless/                 # JS 렌더링이 필요한 탐지
├── default-workflow.yaml     # nuclei 기본 워크플로 템플릿
└── LICENSE
```
+ workflows
  여러 취약점 템플릿을 그룹화하고 논리적인 흐름으로 연결해서 실행하도록 만든 자동화된 스캐닝 시나리오
  <img width="1138" height="484" alt="image" src="https://github.com/user-attachments/assets/10621d62-dc08-43d8-adf6-6a059349cafa" />

##  CVE-2024-55416 분석

- **공격 유형**: Reflected XSS
- **취약 경로**: `/admin/compass?del=...`
- **영향 버전**: Voyager 1.8.0 이하
- **공격 조건**: 로그인된 사용자 + 악성 URL 클릭
- **취약 코드 위치**:
  - `VoyagerCompassController.php`
  - `master.blade.php`

### nuclei 템플릿 주요 구성요소

#### raw
- HTTP 요청을 직접 작성하는 구간
```yaml
raw:
  - |
    POST /admin/login HTTP/1.1
    Host: {{Hostname}}
    Content-Type: application/x-www-form-urlencoded

    _token={{csrf}}&email={{username}}&password={{password}}&
```

#### matchers
- HTTP 응답에서 탐지 성공 여부를 판단하는 조건
```yaml
matchers:
  - type: dsl
    dsl:
      - "contains(body, '/admin</title>')"
      - "status_code == 302"
    condition: and
```

#### extractors
- 응답에서 특정 값을 추출해 변수로 저장
```yaml
extractors:
  - type: regex
    part: body
    name: csrf
    internal: true
    group: 1
    regex:
      - 'name="_token" value="([a-zA-Z0-9]+)"'
```

### nuclei 템플릿 요청 흐름 요약 (CVE-2024-55416 기준)
+ 탐지 cve.yaml : https://github.com/projectdiscovery/nuclei-templates/blob/main/http/cves/2024/CVE-2024-55416.yaml
  
1. **GET /admin/login**
   - CSRF 토큰 추출

2. **POST /admin/login**
   - 로그인 시도 (admin:password 사용)
   - 302 응답 + 세션 유지

3. **GET /admin/compass?del=<XSS payload>**
   - 세션 메시지 삽입 시도
   - 302 응답 확인

4. **GET /admin/compass?logs=true**
   - XSS 성공 여부 확인

### 환경 세팅
#### nuclei 설치
<img width="1232" height="436" alt="image" src="https://github.com/user-attachments/assets/9be60505-ee58-4f5b-ac35-ac5f4f4015fc" />
<img width="1102" height="332" alt="image" src="https://github.com/user-attachments/assets/9110ba7a-0a99-4f9a-9349-af3e625e3f46" />

#### 취약점 환경 세팅
<img width="1464" height="408" alt="image" src="https://github.com/user-attachments/assets/13e2fc67-97e3-49c3-81ec-79a9ea7b02e4" />
<img width="1252" height="436" alt="image" src="https://github.com/user-attachments/assets/a59b4be7-f4ca-40e9-85eb-8d834b7e062e" />
<img width="1228" height="488" alt="image" src="https://github.com/user-attachments/assets/ac0ec1e2-9008-4108-ae60-332b9cf8f123" />

#### 취약점 환경 모습
<img width="1230" height="818" alt="image" src="https://github.com/user-attachments/assets/8533fe4d-2f60-4a95-bbda-785ab650548b" />
<img width="1214" height="730" alt="image" src="https://github.com/user-attachments/assets/7e3cab88-8bc2-479a-96eb-d9ea24195006" />


### 탐지 예시 결과
```
[CVE-2024-55416] [http] [low] http://localhost:8000/admin/compass?logs=true

감지된 취약점 정보:
- 취약 URL: http://localhost:8000/admin/compass?logs=true
- CVE: CVE-2024-55416
- 위험도: Low
- 탐지 결과: matchers 조건 충족
```

<img width="1206" height="476" alt="image" src="https://github.com/user-attachments/assets/c455f646-a3ea-47ad-b5a1-20911b8b0e91" />
<img width="750" height="42" alt="image" src="https://github.com/user-attachments/assets/5cc9dfa6-3ad3-4c96-8805-6a34f7752f09" />



