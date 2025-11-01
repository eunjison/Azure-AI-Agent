# 🤖 Azure AI Agent Workshop

**Microsoft AutoGen과 Azure OpenAI를 활용한 멀티 에이전트 시스템 구축 워크숍**

이 리포지토리는 **AI Agent Workshop**의 실습용 코드와 자료를 제공합니다.
AutoGen 프레임워크를 사용하여 기본 에이전트부터 고급 멀티 에이전트 시스템까지 단계별로 학습할 수 있습니다.

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)
[![AutoGen](https://img.shields.io/badge/AutoGen-0.6.5%2B-green)](https://github.com/microsoft/autogen)
[![Azure OpenAI](https://img.shields.io/badge/Azure%20OpenAI-GPT--4o--mini-orange)](https://azure.microsoft.com/en-us/products/ai-services/openai-service)
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
# [Local에서 수행 시] 1. 저장소 클론 (코드스페이스 사용 시 스킵)
git clone https://github.com/eunjison/Azure-AI-Agent.git
cd Azure-AI-Agent

# 2. Python 가상환경 생성 및 활성화
python3 -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate

# 3. 의존성 패키지 설치
uv pip install -r pyproject.toml

# 4. 환경변수 설정
cp .env.sample .env
# .env 파일에 Azure OpenAI 정보 입력

# 5. Jupyter 커널 등록
python -m ipykernel install --user --name=azure-ai-agent --display-name="Azure AI Agent (Python 3.12)"
```

### 📦 선택적 설치 방법
```bash
# 최소 설치 (Docker 없이)
pip install -e ".[minimal]"

# 개발용 설치 (테스트 도구 포함)
pip install -e ".[dev]"

# 기본 설치 (모든 기능 포함)
pip install -e .
```

### 3️⃣ Azure OpenAI 설정
`.env` 파일에 다음 정보를 입력하세요:
```env
AZURE_OPENAI_ENDPOINT=https://your-resource.openai.azure.com/
AZURE_OPENAI_KEY=your-api-key
AZURE_OPENAI_DEPLOYMENT_NAME=gpt-4o-mini
AZURE_OPENAI_API_VERSION=2025-04-01-preview
SERP_API_KEY=your-serpapi-key  # 웹 검색용 (선택사항)
```

**추가 설정 (선택사항):**
- `GOOGLE_API_KEY`: Google Search API
- `EXCHANGE_RATE_API_KEY`: 환율 데이터 API
- `ALPHA_VANTAGE_API_KEY`: 금융 데이터 API

---

## 📚 실습 노트북 가이드

### 🧭 시작 가이드 & UI 도구
| 파일 | 제목 | 설명 |
|------|------|------|
| `01_Autogen_Studio.md` | AutoGen Studio 가이드 | UI 기반 에이전트 구축 도구 |
| `02_MagenticUI.md` | MagenticUI 가이드 | 고급 멀티 에이전트 UI |

### 🔰 기초 과정 (Basic Agents)
| 노트북 | 제목 | 학습 내용 | 상태 |
|--------|------|-----------|------|
| `03_Basic_Agent.ipynb` | 기본 에이전트 | 단일 에이전트 구현 및 기본 대화 | ✅ 완료 |
| `04_Teams.ipynb` | 팀 기반 에이전트 | RoundRobin 방식 멀티 에이전트 | ✅ 완료 |
| `05_Selector_group_chat.ipynb` | 선택적 그룹챗 | 지능형 발언자 선택 시스템 | ✅ 완료 |

### 🔧 중급 과정 (Advanced Features)
| 노트북 | 제목 | 학습 내용 | 상태 |
|--------|------|-----------|------|
| `06_Research.ipynb` | 연구 에이전트 | 웹 검색 기반 정보 수집 및 분석 | ✅ 완료 |
| `07_code_execution.ipynb` | 코드 실행 에이전트 | AI 코드 생성 및 실행, 주식 분석 | ✅ 완료 |

### 🚀 고급 과정 (Enterprise Systems)  
| 노트북 | 제목 | 학습 내용 | 상태 |
|--------|------|-----------|------|
| `08_MagenticOne.ipynb` | MagenticOne 시스템 | Microsoft 통합 멀티 에이전트 플랫폼 | ✅ 완료 |

### 📋 학습 경로 추천

**🎯 초급자 (AI 에이전트 입문):**
1. `03_Basic_Agent.ipynb` - 기본 개념 학습
2. `04_Teams.ipynb` - 멀티 에이전트 기초
3. `06_Research.ipynb` - 실제 데이터 활용

**🚀 중급자 (실무 응용):**
1. `05_Selector_group_chat.ipynb` - 고급 협업 시스템
2. `07_code_execution.ipynb` - 코드 생성 및 실행
3. `08_MagenticOne.ipynb` - 엔터프라이즈급 시스템

**💼 고급자 (커스터마이징):**
- 기존 노트북을 참고하여 비즈니스 특화 에이전트 개발
- Docker 환경에서 MagenticOne 완전 활용
- 대규모 멀티 에이전트 시스템 아키텍처 설계

---

## 🎯 주요 기능 및 예제

### 🔍 웹 기반 정보 수집 (`06_Research.ipynb`)
```python
# SerpAPI를 활용한 실시간 웹 검색
from autogen_ext.agents.websurfer import WebSurferAgent

web_surfer = WebSurferAgent("WebSurfer", model_client=client)
result = await web_surfer.search("Microsoft 주가 전망 2025")
```

### 📊 AI 코드 생성 및 실행 (`07_code_execution.ipynb`)
```python
# AI가 자동으로 주식 분석 코드를 생성하고 실행
task = "LG CNS, Samsung SDS, SK C&C 주가 비교 분석 차트 생성"
result = await code_executor.run(task)
# 결과: 전문적인 차트 및 상세 분석 리포트
```

### 🤝 멀티 에이전트 협업 (`04_Teams.ipynb`, `05_Selector_group_chat.ipynb`)
```python
# 여러 전문가 에이전트가 협력하여 문제 해결
from autogen_agentchat.teams import RoundRobinGroupChat

team = RoundRobinGroupChat([analyst_agent, researcher_agent, writer_agent])
result = await team.run("IT 서비스 시장 분석 보고서 작성")
```

### 🧠 MagenticOne 통합 시스템 (`08_MagenticOne.ipynb`)
```python
# Microsoft의 통합 멀티 에이전트 플랫폼
from autogen_ext.teams.magentic_one import MagenticOne

m1 = MagenticOne(client=azure_client)
# WebSurfer, FileSurfer, Coder, Executor가 자동 협업
result = await m1.run("마이크로소프트 주가 분석 및 투자 전망 보고서 작성")
```

---

## 📁 프로젝트 구조

```
Azure-AI-Agent/
├── 📋 README.md                        # 프로젝트 가이드 (이 파일)
├── ⚙️ pyproject.toml                  # 패키지 의존성 및 설정 (간소화됨)
├── 🔐 .env                            # 환경변수 (Azure OpenAI 키 설정 완료)
└── 📓 notebooks/                      # Jupyter 실습 노트북
    ├── 01_Autogen_Studio.md           # AutoGen Studio 가이드
    ├── 02_MagenticUI.md               # MagenticUI 가이드  
    ├── 03_Basic_Agent.ipynb           # 기본 에이전트 구현
    ├── 04_Teams.ipynb                 # 팀 기반 멀티 에이전트
    ├── 05_Selector_group_chat.ipynb   # 선택적 그룹챗 시스템
    ├── 06_Research.ipynb              # 웹 검색 연구 에이전트
    ├── 07_code_execution.ipynb        # AI 코드 생성 및 실행 (주식 분석)
    └── 08_MagenticOne.ipynb           # MagenticOne 통합 시스템
```

### 🎯 핵심 특징
- **✅ 완성된 노트북**: 8개 핵심 실습 노트북 모두 동작 확인 완료
- **🔧 간소화된 설정**: 필수 의존성만 포함한 pyproject.toml
- **🔐 바로 사용 가능**: .env 파일에 Azure OpenAI 키 설정 완료
- **📚 점진적 학습**: 기본부터 고급까지 체계적 구성

---

## 🚀 빠른 시작 가이드

### 1️⃣ 첫 번째 에이전트 실행 (5분)
```bash
# VS Code에서 Jupyter 노트북 열기
code notebooks/03_Basic_Agent.ipynb
```
- 커널을 "Azure AI Agent (Python 3.12)"로 선택
- 모든 셀을 순차적으로 실행
- Azure OpenAI 연결 및 기본 대화 테스트

### 2️⃣ 멀티 에이전트 시스템 체험 (10분)
```bash
# 팀 기반 협업 시스템 실습
code notebooks/04_Teams.ipynb
```
- 여러 에이전트가 협력하는 시스템 구현
- RoundRobin 방식의 토론 시스템 체험

### 3️⃣ 실제 데이터 활용 (15분)
```bash
# 웹 검색 기반 연구 에이전트
code notebooks/06_Research.ipynb
```
- SerpAPI를 활용한 실시간 웹 검색
- 실제 정보를 수집하고 분석하는 AI 에이전트

### 4️⃣ AI 코드 생성 및 실행 (20분)
```bash
# 주식 분석 자동화 시스템
code notebooks/07_code_execution.ipynb
```
- AI가 자동으로 주식 분석 코드 생성
- 실시간 데이터 수집 및 전문적인 차트 생성

### 5️⃣ 엔터프라이즈급 시스템 (30분)
```bash
# MagenticOne 통합 플랫폼
code notebooks/08_MagenticOne.ipynb
```
- Microsoft의 차세대 멀티 에이전트 시스템
- WebSurfer, Coder, Executor가 자동 협업

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

### 🚨 자주 발생하는 문제 및 해결방법

#### 1️⃣ 패키지 설치 오류
```bash
# 해결방법: 가상환경 재생성 및 패키지 재설치
rm -rf .venv
python3 -m venv .venv
source .venv/bin/activate
uv pip install -r pyproject.toml
```

#### 2️⃣ Jupyter 커널 인식 안됨
```bash
# 커널 재등록
python -m ipykernel install --user --name=azure-ai-agent --display-name="Azure AI Agent (Python 3.12)"
# VS Code에서 커널 선택: "Azure AI Agent (Python 3.12)"
```

#### 3️⃣ Azure OpenAI 연결 오류
```python
# .env 파일 확인
import os
from dotenv import load_dotenv
load_dotenv()

print("Endpoint:", os.getenv("AZURE_OPENAI_ENDPOINT"))
print("Key exists:", bool(os.getenv("AZURE_OPENAI_KEY")))
print("Deployment:", os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"))
```

#### 4️⃣ MagenticOne Docker 오류
```bash
# 방법 1: Docker 패키지 설치
pip install 'autogen-ext[docker]'
pip install asyncio-atexit docker

# 방법 2: 간소화 버전 사용 (08_MagenticOne.ipynb 두 번째 셀)
# Docker 없이도 멀티 에이전트 시스템 체험 가능
```

#### 5️⃣ 한글 폰트 경고 (matplotlib)
```python
# 이미 해결됨 - 모든 노트북에서 영어 폰트 사용
import matplotlib.pyplot as plt
plt.rcParams['font.family'] = 'DejaVu Sans'
```


---

## 🎓 학습 리소스

### 📚 공식 문서
- [AutoGen 공식 문서](https://microsoft.github.io/autogen/)
- [Azure OpenAI 서비스](https://azure.microsoft.com/en-us/products/ai-services/openai-service)
- [MagenticOne 논문](https://www.microsoft.com/en-us/research/project/magentic-one/)

### 🎥 추천 학습 자료
- [AutoGen GitHub](https://github.com/microsoft/autogen)
- [Python for AI Development](https://docs.python.org/3/tutorial/)
- [Jupyter Notebook 가이드](https://jupyter.org/documentation)

### � 커뮤니티
- [AutoGen Discord](https://discord.gg/autogen)
- [Microsoft AI Community](https://techcommunity.microsoft.com/t5/ai-and-machine-learning/ct-p/AIMachineLearning)

---

## 🤝 기여하기

버그 리포트, 기능 제안, 또는 개선사항이 있으시면 언제든지 Issue를 생성해주세요!

**🎉 Happy Agent Building! 🤖**


