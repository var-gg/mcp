# VARGG MCP

[![MCP Protocol](https://img.shields.io/badge/MCP-Protocol-blue)](https://modelcontextprotocol.io)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Discussions](https://img.shields.io/badge/discussions-welcome-blue)](https://github.com/var-gg/mcp/discussions)

**Languages / 语言 / 言語 / 언어 / Ngôn ngữ:**
- [![English](https://img.shields.io/badge/English-Click-yellow)](README.md)
- [![한국어](https://img.shields.io/badge/한국어-클릭-yellow)](README-ko.md)
- [![日本語](https://img.shields.io/badge/日本語-クリック-blue)](README-ja.md)
- [![简体中文](https://img.shields.io/badge/简体中文-点击查看-orange)](README-zh.md)
- [![Tiếng Việt](https://img.shields.io/badge/Tiếng_Việt-Nhấn_vào-green)](README-vi.md)

> **Model Context Protocol를 통한 프로젝트 메타데이터 관리 도구**

프로젝트별로 변수명, 상수, 표준 용어를 체계적으로 관리하고, Cursor IDE와 통합하여 LLM이 일관된 명명 규칙을 사용하도록 돕습니다.

---

## 🎯 개요

VARGG MCP는 개발 환경과 중앙화된 프로젝트 메타데이터 관리 시스템 간의 원활한 통합을 가능하게 하는 Model Context Protocol 구현입니다. 특히 Cursor IDE와 같은 AI 어시스턴트로 작업할 때 프로젝트 전반에 걸쳐 일관된 명명 규칙을 유지하는 데 도움이 됩니다.

### 해결하는 문제들

- **일관성 없는 명명**: 개발자마다 동일한 개념에 대해 다른 변수명을 사용
- **언어 장벽**: 여러 언어로 작업하는 팀이 용어 일관성을 유지하기 어려움
- **AI 컨텍스트 손실**: LLM이 팀의 기존 규칙을 모른 채 코드 생성
- **지식 고립**: 프로젝트별 명명 패턴이 공유되지 않거나 발견되지 않음
- **온보딩 어려움**: 새로운 팀원이 어떤 명명 규칙을 따라야 할지 모름

### 주요 기능 요약

- **프로젝트 기반 구성**: 프로젝트별로 변수와 상수 관리
- **다국어 지원**: 한국어, 영어, 일본어, 중국어, 베트남어 네이티브 지원
- **Cursor IDE 통합**: MCP 프로토콜을 통한 Cursor IDE 직접 통합
- **실시간 검색**: 기존 변수와 정의를 즉시 검색
- **표준 용어**: 프로젝트 전반에 걸쳐 일관된 정의 유지
- **팀 협업**: 팀 내에서 명명 패턴 공유 및 발견

### 대상 사용자

- **개발 팀**: 일관된 명명 규칙을 유지하고 싶은 팀
- **다국어 프로젝트**: 여러 언어 및 로케일을 포함하는 프로젝트
- **AI 지원 개발**: Cursor IDE 또는 유사한 AI 코딩 어시스턴트를 사용하는 개발자
- **프로젝트 관리자**: 프로젝트 전반에 걸쳐 표준화된 용어를 관리하는 팀

---

## ✨ 주요 기능

### 🗂️ 프로젝트 기반 변수 관리
변수와 상수를 프로젝트별로 구성하여 프로젝트별 명명 규칙을 쉽게 유지하면서 팀 간 공통 패턴을 공유할 수 있습니다.

### 🌐 다국어 지원
5개 언어 완전 지원:
- 🇰🇷 한국어 (ko)
- 🇺🇸 영어 (en)
- 🇯🇵 일본어 (ja)
- 🇨🇳 중국어 (zh)
- 🇻🇳 베트남어 (vi)

각 언어는 변수명과 정의에 대한 고유한 검증 규칙과 문자 집합을 가지고 있습니다.

### 🔌 Cursor IDE 통합
Model Context Protocol을 통한 Cursor IDE와의 원활한 통합. LLM이 코드를 생성할 때 팀의 표준 용어를 자동으로 검색하고 사용할 수 있습니다.

### 🔍 자동 표준 용어 검색 및 제안
LLM이 코드를 생성할 때 프로젝트의 변수 라이브러리를 검색하고 새로운 것을 만들기보다 기존 표준 용어를 제안합니다.

### ⚡ 실시간 변수 검색 및 등록
기존 변수를 즉시 검색하고 작업 중에 새로운 변수를 등록합니다. 모든 작업은 MCP 프로토콜을 통해 실시간으로 수행됩니다.

---

## 🚀 빠른 시작

### 필요 조건

- Cursor IDE 설치됨
- VARGG 계정 ([var.gg](https://var.gg)에서 생성)
- VARGG 웹사이트에서 API 키

### 1. API 키 받기

1. [var.gg](https://var.gg)를 방문하고 로그인
2. 계정 설정으로 이동
3. MCP 액세스를 위한 API 키 생성

### 2. Cursor IDE 구성

Cursor IDE 설정에 VARGG MCP 추가:

**파일(F) > 기본 설정 > Cursor 설정**

다음 구성을 추가:

```json
{
  "mcpServers": {
    "vargg": {
      "url": "https://var.gg/mcp/ko/project",
      "headers": {
        "X-API-KEY": "your-api-key-here"
      }
    }
  }
}
```

**참고**: `ko`를 선호하는 로케일(`en`, `ja`, `zh`, `vi`)로 교체하세요.

1단계에서 받은 실제 API 키로 `your-api-key-here`를 교체하세요.

### 3. 첫 프로젝트 생성

Cursor IDE에서 AI 어시스턴트에게 요청:

```
"E-Commerce Payment"라는 이름으로 "전자상거래 플랫폼용 결제 처리 모듈" 설명과 함께 새 프로젝트 생성
```

또는 [var.gg/projects](https://var.gg/projects)에서 웹 인터페이스를 사용하세요.

### 4. 변수 사용 시작

Cursor에게 변수를 검색하거나 생성하도록 요청:

```
프로젝트에서 "사용자 계정"과 관련된 변수 검색
```

```
프로젝트에서 "전체 개수" 정의를 가진 약어 변수 TOTAL_COUNT 생성
```

---

## 🛠️ 사용 가능한 도구

VARGG MCP는 프로젝트와 변수를 관리하기 위한 다음 도구를 제공합니다:

### 프로젝트 관리
- **`projects`** - 접근 가능한 모든 프로젝트 나열
- **`create_project`** - 새 프로젝트 생성
- **`update_project`** - 프로젝트 정보 업데이트
- **`open_project_admin`** - 권한 및 사용자 초대를 위한 프로젝트 관리 페이지 열기

### 변수 관리
- **`search_variables`** - 프로젝트 내 변수 검색
- **`create_variables`** - 프로젝트에 새 변수 생성
- **`list_variables`** - 프로젝트의 모든 변수 나열 (페이징)
- **`remove_variables`** - 프로젝트에서 변수 제거

각 도구에 대한 자세한 문서는 [도구 참조](docs/tools-reference.md)를 참조하세요.

---

## 📖 문서

- **[시작하기](docs/getting-started.md)** - 상세한 설정 가이드
- **[도구 참조](docs/tools-reference.md)** - 모든 도구에 대한 완전한 API 문서
- **[Cursor 통합 가이드](docs/integration-guide.md)** - 단계별 Cursor IDE 설정
- **[모범 사례](docs/best-practices.md)** - 권장 워크플로우 및 패턴
- **[사용 사례](examples/use-cases.md)** - 실제 예제 및 시나리오
- **[공식 웹사이트](https://var.gg)** - 인터랙티브 데모 및 상세 가이드

---

## 💡 사용 사례

### 팀 내 명명 규칙 통일
모든 팀원이 공통 개념에 대해 동일한 변수명을 사용하도록 보장합니다. 예를 들어 `UserAccount`, `userAccount`, `user_account` 등을 혼합하는 대신 항상 `USER_ACCOUNT`를 사용합니다.

### 프로젝트별 표준 용어 관리
각 프로젝트는 고유한 표준 용어 집합을 가질 수 있습니다. "Payment" 프로젝트는 `PAYMENT_AMOUNT`를 가질 수 있고, "Shipping" 프로젝트는 `SHIPPING_COST`를 가질 수 있습니다.

### LLM 코드 생성의 일관성 보장
Cursor에게 코드 생성을 요청하면 프로젝트의 변수 라이브러리를 검색하고 기존 표준 용어를 사용하여 생성된 모든 코드에서 일관성을 유지합니다.

### 다국어 프로젝트의 변수명 관리
다국어 지원은 코드의 영어 변수명을 유지하면서 모국어로 변수를 정의할 수 있음을 의미합니다. 예를 들어 한국어 정의 "전체 개수"를 가진 `TOTAL_COUNT`.

---

## 🤝 커뮤니티

- **[Issues](https://github.com/var-gg/mcp/issues)**: 버그 신고, 기능 제안, 질문
- **[Discussions](https://github.com/var-gg/mcp/discussions)**: 팁 공유, Q&A, 아이디어 토론
- **로드맵**: 계획된 기능 및 개선 사항 확인 (이슈 레이블 확인)

### 기여 방법

1. [Discussions](https://github.com/var-gg/mcp/discussions)에서 사용 사례 공유
2. [Issues](https://github.com/var-gg/mcp/issues)를 통해 버그 신고 또는 기능 요청
3. "Show and Tell" 카테고리에서 모범 사례 공유

---

## 🌐 다국어 지원

VARGG MCP는 네이티브 검증 및 문자 집합을 가진 다음 언어를 지원합니다:

| Language | Code | Character Set |
|----------|------|---------------|
| 🇰🇷 한국어 | `ko` | 한글 + 영문 + 숫자 + 공백 + 괄호 |
| 🇺🇸 영어 | `en` | English letters + numbers + spaces |
| 🇯🇵 일본어 | `ja` | ひらがな + カタカナ + 漢字 + 영문 + 숫자 |
| 🇨🇳 중국어 | `zh` | 汉字 + 영문 + 숫자 |
| 🇻🇳 베트남어 | `vi` | Vietnamese + 영문 + 숫자 |

각 언어는 변수명과 정의에 대한 특정 검증 규칙을 가지고 있습니다. 자세한 내용은 [도구 참조](docs/tools-reference.md)를 참조하세요.

---

## 🔗 링크

- **웹사이트**: [https://var.gg](https://var.gg)
- **MCP 가이드**: [https://var.gg/ko/mcp](https://var.gg/ko/mcp) (en, ja, zh, vi에서도 사용 가능)
- **인터랙티브 데모**: [https://var.gg/[locale]/mcp](https://var.gg/ko/mcp) - 브라우저에서 도구 시도
- **이슈 신고**: [https://github.com/var-gg/mcp/issues](https://github.com/var-gg/mcp/issues)
- **토론**: [https://github.com/var-gg/mcp/discussions](https://github.com/var-gg/mcp/discussions)

---

## 📝 라이선스

이 프로젝트는 MIT 라이선스 하에 라이선스됩니다 - 자세한 내용은 [LICENSE](LICENSE) 파일을 참조하세요.

---

## ⚠️ 중요 참고 사항

### 코드 공개

현재 이 저장소는 문서 및 커뮤니티 리소스만 포함합니다. MCP 서버 구현 코드는 아직 오픈 소스가 아니지만, 향후 공개할 수 있습니다. 업데이트를 확인하세요!

### 아키텍처 참고

VARGG MCP 구현은 JSON-RPC 2.0 프로토콜 인터페이스를 사용합니다. Cursor IDE는 JSON-RPC 2.0을 사용하여 MCP 서버와 통신하고, 이는 백엔드로 REST API 호출로 변환됩니다. 프론트엔드는 Cursor의 MCP 프로토콜과 백엔드 REST API 간의 프록시 계층 역할을 합니다.

### 버전 관리

코드가 공개되지 않았더라도 [CHANGELOG.md](CHANGELOG.md)에서 MCP 도구 버전 및 기능 변경 사항을 추적합니다.

### 개인정보 보호

이슈를 신고하거나 기능을 논의할 때 개인 정보나 API 키를 공유하지 마세요. 민감한 정보를 공유해야 하는 경우 개인적으로 연락하세요.

---

**VARGG 팀이 ❤️로 만들었습니다**

