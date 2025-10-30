# 🧠 AutogenUI Studio의 Gallery를 활용한 Agent 생성 예제

---

## 1️⃣ 개요 (Overview)

이 가이드는 **Microsoft AutoGenUI (AutoGen Studio)** 를 통해 코드없이 실행가능한 **LLM 기반 에이전트(Agent)**를 만드는 방법을 담고 있습니다.

* **AutoGen Studio 버전:** v0.4.x
* **참고 문서:** [GitHub: microsoft/autogen](https://github.com/microsoft/autogen/tree/main/python/packages/autogen-studio)



📌 이 문서는 화면 캡처, CLI 명령어, 설정 형식, 에이전트 해설을 모두 포함합니다.

---

### 클라이언트 설치

```bash
# AutoGen Studio 설치
pip install -U autogenstudio
```

---

## Autogen Studio 실행 (Launch)

```bash
autogenstudio ui --port 8080 --appdir ./myapp
```

➡️ [http://localhost:8080](http://localhost:8080) 에서 레이어 시작

📸 **캡처 1:** 시작 화면(`Welcome to AutoGen Studio`)

> 💡 **Tip:** `--appdir` 옵션은 프로젝트별 구성 복사에 유용합니다.
![alt text](image-1.png)
---


## [예제1] AssistantAgent 예제 (기본 대화형 에이전트)

이 예제는 **Gallery** 내의 템플릿 중 하나인 **AssistantAgent**를 활용하여, 사용자의 질의에 답변하는 단일 에이전트를 만드는 과정을 보여줍니다.

### 단계별 가이드

#### 1. Studio 실행 및 Gallery 열기

```bash
autogenstudio ui --port 8080
```

➡️ 브라우저에서 [http://localhost:8080](http://localhost:8080) 접속 후, 좌측 메뉴의 **Gallery** 탭 선택

📸 **캡처 1:** Gallery 첫 화면 (AssistantAgent 템플릿 카드 표시)

#### 2. AssistantAgent 템플릿 선택

* Gallery에서 **AssistantAgent**를 클릭합니다.
* 오른쪽 패널에 미리 구성된 에이전트 정보가 표시됩니다.

📸 **캡처 2:** AssistantAgent 세부 정보 화면

#### 3. 템플릿 불러오기 및 구성 수정

* **“Use this Template”** 버튼 클릭
* 다음 항목 수정:
  * **모델 변경:** `AzureOpenAI GPT-4o-mini`
  * **Model:** `env 파일과 동일`
  * **API Key:** `env 파일과 동일`
  * **Azure Endpoint:** `env 파일과 동일`
  * **Azure Deployment:** `env 파일과 동일`
  * **System Prompt:** “당신은 친절하고 유익한 AI 비서입니다.”

📸 **캡처 3:** 에이전트 편집 화면 (System Prompt 입력 부분 강조)

#### 4. 에이전트 실행

* 상단의 ▶ **Run** 버튼 클릭
* 예시 프롬프트: “오늘 서울 날씨 알려줘.”

📸 **캡처 4:** 대화 결과 표시 화면

#### 5. 결과 저장

* **Export as JSON** 선택 → `assistant_agent_demo.json` 파일 저장

> 💡 **Tip:** AssistantAgent 템플릿은 단일 LLM과 직접 상호작용하는 기본형으로, RAG나 Tool 호출 없이 간단한 QA/대화형 기능에 적합합니다.

---

## [예제2] Deep Research Team 예제 (다중 에이전트 협업)

이 예제는 **Gallery**의 고급 템플릿 중 하나인 **Deep Research Team**을 활용하여, 여러 에이전트가 협업하며 정보를 수집하고 보고서를 작성하는 구조를 보여줍니다.

### 단계별 가이드

#### 1. Gallery에서 Deep Research Team 선택

* 좌측 메뉴 → **Gallery** 클릭
* **Deep Research Team** 템플릿 카드 선택

📸 **캡처 5:** Deep Research Team 템플릿 카드 표시

#### 2. 템플릿 불러오기

* “Use this Template” 클릭 → 프로젝트 이름 지정: `deep_research_team_demo`

📸 **캡처 6:** 템플릿 불러오기 후 팀 구조 다이어그램 표시

#### 3. 팀 구성 검토 및 수정

| 역할             | 설명              |
| -------------- | --------------- |
| **Researcher** | 검색 및 자료 수집 담당   |
| **Writer**     | 내용을 요약 및 보고서 작성 |
| **Reviewer**   | 최종 문장 품질 검토     |

* 각 Agent의 System Prompt를 아래와 같이 수정합니다.

```text
Researcher: “사용자의 질문을 이해하고 최신 정보를 수집합니다.”
Writer: “Researcher가 제공한 자료를 논리적 보고서로 정리합니다.”
Reviewer: “Writer의 결과를 검토하고 문법 및 표현을 다듬습니다.”
```

📸 **캡처 7:** Workflow Builder에서 세 에이전트 연결선 표시 (Researcher → Writer → Reviewer)

#### 4. 실행 및 결과 확인

* 상단의 ▶ **Run** 클릭
* 예시 프롬프트: “2025년 한국의 AI 산업 동향을 요약해줘.”

📸 **캡처 8:** 실행 로그 및 단계별 협업 결과 화면

#### 5. 결과 저장 및 공유

* **Export → JSON** 파일로 저장 (`deep_research_team_demo.json`)
* 또는 **Share via URL** 기능 사용하여 링크 공유

> 💡 **Tip:** Deep Research Team 템플릿은 다중 에이전트 협업 구조를 자동 구성하며, 각 에이전트의 역할이 분리되어 복잡한 연구나 리포트 작성 작업에 적합합니다.

---

## 🔧 요약 비교

| 항목         | AssistantAgent  | Deep Research Team   |
| ---------- | --------------- | -------------------- |
| 구조         | 단일 에이전트         | 3개 에이전트 협업           |
| 사용 모델      | GPT-4o-mini     | GPT-4o / GPT-4-turbo |
| 목적         | 간단한 질의응답        | 심층 분석 및 보고서 작성       |
| Gallery 위치 | Basic Templates | Advanced Templates   |
| 실행 복잡도     | 낮음              | 높음 (협업 시퀀스)          |

---

📘 **참고:** Gallery 템플릿은 AutoGen Studio 버전에 따라 구성이 다를 수 있습니다.
문서 작성 시 각 화면의 버전을 하단에 명시하는 것을 권장합니다.

> 예: *본 예제는 AutoGen Studio v0.4.2 기준으로 작성되었습니다.*



