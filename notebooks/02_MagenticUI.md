# 🧲 Magentic UI를 사용한 에이전트 구현 예제

---

## 1️⃣ 개요 (Overview)

이 가이드는 *MMagentic UI** 를 통해 코드없이 실행가능한 **LLM 기반 에이전트(Agent)**를 만드는 방법을 담고 있습니다.
Magentic UI는 사람이 중간에 개입할 수 있는(human-in-the-loop) 웹 에이전트 UI입니다.
AutoGen 위에서 돌아가고, 실행 전에 Plan을 보여주고, 민감한 액션은 승인받고, 실행 결과는 채팅으로 보여주는 구조예요. 웹을 실제로 열어서 작업하는 데 강점이 있습니다.

---

### 클라이언트 설치

```bash
# AutoGen Studio 설치
pip install magentic-ui --upgrade

# 도커 없이 UI 실행하기
magentic-ui --run-without-docker --port 8081
```
➡️ 브라우저에서 http://localhost:8081
 열기
📸 캡처 M-1: 첫 화면(세션 목록 + 우측 채팅 패널이 보이게) 
![alt text](image.png)
GitHub
---

# 🧲 Magentic UI를 사용한 에이전트 구현 예제

(출처: [microsoft/magentic-ui](https://github.com/microsoft/magentic-ui) 기준, 2025-10-30 버전)

Magentic UI는 **사람이 중간에 개입할 수 있는(human-in-the-loop)** 웹 에이전트 UI입니다. AutoGen 위에서 작동하며, 실행 전에 Plan을 보여주고 사용자의 승인을 받은 뒤 실제 웹 동작을 수행합니다. 이 섹션에서는 **단일 에이전트 예제**와 **MCP 연동 예제** 두 가지를 다룹니다.

---

## 예제 1: 단일 에이전트로 웹 작업 자동화하기

### 🎯 목적

* MCP 없이 LLM + 브라우저 액션만으로 간단한 자동화 수행
* "계획 → 승인 → 실행 → 결과" 흐름을 한눈에 시연

### 🧩 단계

1. **New Session** 클릭 → 세션 이름: `single-agent-demo`
2. 우측 채팅창에 프롬프트 입력:

   > “마이크로소프트 리서치 블로그에서 Magentic UI 관련 글을 찾아서 요약해줘.”
3. Magentic UI가 **Plan**을 자동 생성합니다.

   * 예: (1) 웹페이지 열기 → (2) 본문 추출 → (3) 요약
4. 각 단계별 **Approve / Edit** 버튼을 사용해 승인
5. 승인 후 실제 브라우저 탭이 열려 페이지를 탐색합니다.
6. 실행이 완료되면 요약 결과가 채팅에 표시됩니다.

📸 Plan 생성 화면 (Approve 버튼 표시)
📸 실행 후 요약 결과가 표시된 화면

### 💡 포인트

* MCP 없이 **단일 에이전트로도 완전한 웹 자동화** 구현 가능
* **Action Guard** 기능으로 민감한 작업은 반드시 사용자 승인 필요

---

## 예제 2: MCP를 활용한 에이전트 확장

Magentic UI는 **MCP (Model Context Protocol)** 서버를 연결해 로컬 시스템이나 외부 데이터를 활용할 수 있습니다.

### ⚙️ 사전 조건

* MCP 서버 실행 중 (`localhost:9000` 예시)
* Magentic UI MCP 플러그인 설치 필요

  ```bash
  pip install "magentic-ui[mcp]"
  ```

### 🧩 단계

1. Magentic UI 실행
2. 좌측 메뉴 → **Settings → MCP / Agent Sources** 진입
3. 새 연결 추가:

   * **Name:** `local-mcp`
   * **Endpoint:** `http://localhost:9000`
   * **Auth:** 필요 시 토큰 입력
4. 연결 성공 후 새 세션 생성 → 프롬프트 입력:

   > “로컬 MCP가 제공하는 프로젝트 목록을 가져오고, 최신 항목을 웹에서 검색하여 요약해줘.”
5. 생성된 Plan을 확인:

   * Step 1: MCP 호출 (데이터 가져오기)
   * Step 2: 웹 탐색 (추가 정보 수집)
   * Step 3: 요약 작성
6. 각 Step 승인 후 실행 → 최종 통합 리포트 확인

📸 **캡처 M-4:** MCP 연결 설정 화면
📸 **캡처 M-5:** MCP + Web Step이 모두 포함된 Plan 화면
📸 **캡처 M-6:** 최종 결과가 표시된 채팅 화면

### 💡 포인트

* MCP 통합으로 **조직 내부 리소스나 로컬 데이터 접근 가능**
* 모든 액션은 human-in-the-loop 승인 절차를 거쳐 안전하게 수행

---

## 4️⃣ Autogen Studio와의 비교 정리

| 구분     | Autogen Studio   | Magentic UI                     |
| ------ | ---------------- | ------------------------------- |
| 주요 목적  | 에이전트 및 워크플로 설계   | 웹 기반 에이전트 실행 및 조정               |
| 사용자 개입 | 설계 단계 중심         | 실행 단계 중심 (Plan → Approve → Run) |
| 특징     | 다중 에이전트 협업 구조    | 실시간 웹 브라우저 제어 가능                |
| 확장성    | 템플릿, JSON Export | MCP, 브라우저 액션, 플러그인              |

> 📝 *이 문서는 microsoft/magentic-ui 저장소 main 브랜치를 기준으로 2025-10-30에 작성되었습니다. 이후 CLI 및 UI 명칭은 변경될 수 있습니다.*

