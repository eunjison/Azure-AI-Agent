# 🤖 Azure AI Agent Workshop (2Day)

**Microsoft AutoGen과 Azure OpenAI를 활용한 멀티 에이전트 시스템 구축 워크숍**

이 Git Repository는 **AI Agent Workshop (2일 워크숍)**의 실습용 코드와 자료를 담기 위한 Repo입니다.
워크숍 참여자는 이 저장소를 복제(clone)한 뒤, 아래 실습 스크립트를 순차적으로 실행하며 학습 과정을 따라가시면 됩니다.

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)
[![AutoGen](https://img.shields.io/badge/AutoGen-0.2%2B-green)](https://github.com/microsoft/autogen)
[![Azure OpenAI](https://img.shields.io/badge/Azure%20OpenAI-GPT--4o-orange)](https://azure.microsoft.com/en-us/products/ai-services/openai-service)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## 📋 워크숍 개요

### 🎯 학습 목표
- **단일 에이전트**에서 **멀티 에이전트 시스템**까지 점진적 학습
- **Azure OpenAI** 서비스와 **AutoGen 프레임워크** 실무 활용
- **실제 비즈니스 시나리오**에 적용 가능한 AI 에이전트 구현
- **웹 검색, 파일 처리, 코드 실행** 등 다양한 기능 통합

### 🏗️ 워크숍 구조
```
📚 Basic Concepts     → 🔧 Advanced Features    → 🚀 Real-world Applications
단일 에이전트 구현      멀티 에이전트 협업          비즈니스 시나리오 적용
메모리 관리             팀 기반 작업 분배          MagenticOne 통합 시스템
API 통합               코드 실행 에이전트         고객 서비스 자동화
```

---

## 🛠️ 환경 설정

### 1️⃣ 필수 요구사항
- **Python 3.9+** (권장: 3.11 또는 3.12)
- **Azure OpenAI** 서비스 접근 권한
- **Visual Studio Code** + Jupyter Extension
- **GitHub 계정**

### 2️⃣ 설치 및 설정
```bash
# 1. 저장소 클론
git clone https://github.com/eunjison/Azure-AI-Agent.git
cd Azure-AI-Agent

# 2. Python 가상환경 생성 (권장)
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate

# 3. 의존성 패키지 설치
uv pip install -r pyproject.toml

# 4. 환경변수 설정
cp .env.sample .env
# .env 파일에 Azure OpenAI 정보 입력
```

### 3️⃣ Azure OpenAI 설정
`.env` 파일에 다음 정보를 입력하세요:
```env
AZURE_OPENAI_ENDPOINT=https://your-resource.openai.azure.com/
AZURE_OPENAI_KEY=your-api-key
AZURE_OPENAI_DEPLOYMENT_NAME=gpt-4o-mini
AZURE_OPENAI_API_VERSION=2024-02-15-preview
SERP_API_KEY=your-serpapi-key  # 웹 검색용 (선택사항)
```

---

## 📚 실습 노트북 가이드

### 🔰 기초 과정 (Basic)
| 노트북 | 제목 | 학습 내용 | 난이도 |
|--------|------|-----------|--------|
| `03_basic_agent.ipynb` | 기본 에이전트 | 프롬프트-응답 기반 단일 에이전트 | ⭐ |
| `04_memory_agent.ipynb` | 메모리 에이전트 | 대화 기록 관리 및 컨텍스트 유지 | ⭐⭐ |
| `05_api_integration.ipynb` | API 통합 | 외부 API 연동 및 실시간 데이터 활용 | ⭐⭐ |

### 🔧 중급 과정 (Intermediate)
| 노트북 | 제목 | 학습 내용 | 난이도 |
|--------|------|-----------|--------|
| `07_multi-agent_basic.ipynb` | 멀티 에이전트 기초 | 여러 에이전트 간 협업 시스템 | ⭐⭐⭐ |
| `08_teams.ipynb` | 팀 기반 협업 | RoundRobin 방식 에이전트 팀 구성 | ⭐⭐⭐ |
| `09_selector_group_chat.ipynb` | 선택적 그룹챗 | 지능형 발언자 선택 시스템 | ⭐⭐⭐ |
| `10_research.ipynb` | 연구 에이전트 | 웹 검색 기반 정보 수집 및 분석 | ⭐⭐⭐ |

### 🚀 고급 과정 (Advanced)
| 노트북 | 제목 | 학습 내용 | 난이도 |
|--------|------|-----------|--------|
| `11_code_execution.ipynb` | 코드 실행 에이전트 | 동적 코드 생성 및 실행 시스템 | ⭐⭐⭐⭐ |
| `12_MagenticOne.ipynb` | MagenticOne 통합 | Microsoft의 통합 멀티 에이전트 플랫폼 | ⭐⭐⭐⭐⭐ |

---

## 🎯 주요 학습 시나리오

### 🌐 웹 기반 정보 수집 (Research Agent)
```python
# SerpAPI를 활용한 실시간 웹 검색
agent = ResearchAgent()
result = await agent.search("Microsoft 주가 전망 2025")
```

### 📊 데이터 분석 및 시각화 (Code Execution)
```python
# AI가 자동으로 코드를 생성하고 실행
task = "2024년 이후 MSFT와 AAPL 주가 비교 차트 생성"
result = await code_agent.execute(task)
```

### 🤝 멀티 에이전트 협업 (Team Based)
```python
# 여러 전문가 에이전트가 협력하여 문제 해결
team = RoundRobinGroupChat([analyst, researcher, writer])
result = await team.solve("시장 분석 보고서 작성")
```

### 🧠 MagenticOne 통합 시스템
```python
# Microsoft의 차세대 멀티 에이전트 플랫폼
m1 = MagenticOne(client=azure_client)
result = await m1.run("복잡한 비즈니스 문제 해결")
```

---

## 📁 프로젝트 구조

```
Azure-AI-Agent/
├── 📋 README.md                    # 프로젝트 가이드 (이 파일)
├── ⚙️ pyproject.toml              # 패키지 의존성 및 설정
├── 🔐 .env.sample                 # 환경변수 템플릿
├── 🔐 .env                        # 실제 환경변수 (개인 설정)
├── 📓 notebooks/                  # Jupyter 실습 노트북
│   ├── 03_basic_agent.ipynb       # 기본 에이전트 구현
│   ├── 04_memory_agent.ipynb      # 메모리 관리 에이전트
│   ├── 05_api_integration.ipynb   # API 통합 (SerpAPI)
│   ├── 07_multi-agent_basic.ipynb # 멀티 에이전트 기초
│   ├── 08_teams.ipynb             # 팀 기반 협업
│   ├── 09_selector_group_chat.ipynb # 선택적 그룹챗
│   ├── 10_research.ipynb          # 웹 검색 연구 에이전트
│   ├── 11_code_execution.ipynb    # 코드 실행 에이전트
│   └── 12_MagenticOne.ipynb       # MagenticOne 통합
└── 🗂️ .venv/                     # Python 가상환경
```

---

## 🚀 빠른 시작 가이드

### 1️⃣ 첫 번째 에이전트 실행
```bash
# VS Code에서 Jupyter 노트북 열기
code notebooks/03_basic_agent.ipynb
```

### 2️⃣ Azure OpenAI 연결 테스트
```python
from openai import AzureOpenAI
client = AzureOpenAI(
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_KEY"),
    api_version="2024-02-15-preview"
)
```

### 3️⃣ 첫 번째 멀티 에이전트 시스템
```python
from autogen_agentchat.teams import RoundRobinGroupChat
team = RoundRobinGroupChat([agent1, agent2])
result = await team.run("AI의 미래에 대해 토론해주세요")
```

---

## 🛡️ 보안 및 모범 사례

### 🔐 API 키 관리
- ✅ `.env` 파일에 API 키 저장 (Git에 커밋 금지)
- ✅ `python-dotenv`로 환경변수 로드
- ❌ 코드에 직접 API 키 하드코딩 금지

### 🚦 레이트 리밋 관리
- Azure OpenAI 사용량 모니터링
- 적절한 지연 시간 설정
- 에러 핸들링 및 재시도 로직 구현

### 🧪 코드 실행 보안
- Local Code Executor 사용 시 주의
- 신뢰할 수 없는 코드 실행 방지
- Docker 환경 사용 권장 (프로덕션)

---

## 🔧 트러블슈팅

### 자주 발생하는 문제들

#### 1. ModuleNotFoundError
```bash
# 해결방법: 패키지 재설치
pip install -e .
```

#### 2. Azure OpenAI 연결 오류
```python
# .env 파일 확인
print(os.getenv("AZURE_OPENAI_ENDPOINT"))
```

#### 3. MagenticOne 의존성 문제
```bash
# 추가 패키지 설치
pip install markitdown playwright aiofiles pillow
playwright install
```


---

## 📄 라이센스
---
이 프로젝트의 일부는 [MIT License](LICENSE) 하에 배포됩니다.


---

**🎉 Happy Agent Building! 🤖**


