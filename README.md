# Azure AI Agent Workshop (2Day)

이 Git Repository는 **LG AI Agent Workshop (2일 워크숍)**의 실습용 코드와 자료를 담기 위한 Repo입니다.  
워크숍 참여자는 이 저장소를 복제(clone)한 뒤, 아래 실습 스크립트를 순차적으로 실행하며 학습 과정을 따라가시면 됩니다.

## 워크숍 개요

- **목표**: AI 에이전트를 설계하고 구현해보며, 직접 AI Agent 개발과 활용을 경험할 수 있는 예제를 실습  
- **주요 내용**
- Day 1: AI Agent 개념 이해 및 체험
- Day 2: 실제 환경에서 AI Agent 실습과 고도화

---

## 🧰 실습 환경 준비

- Python 3.8 이상 설치
- 가상환경 사용 권장 (`venv`)
- VS Code 또는 Jupyter Notebook
- 주요 패키지 (예: `openai`, `requests`, `flask` 등)  
- Git 클라이언트 및 GitHub 계정  

```bash
# 예: 가상환경 생성 및 활성화 (Unix/macOS 기준)
python3 -m venv venv
source venv/bin/activate

# 필요한 패키지 설치
pip install -r requirements.txt

## 실습 예제
본 리포지토리에는 AI Agent 구축의 핵심 예제 스크립트를 포함합니다.

---

## 빠른 시작
1. 리포지토리 클론

## 폴더 구조
Azure-AI-Agent-Workshop/
│
├─ README.md
├─ requirements.txt
├─ .gitignore
├─ notebooks/
│    └─ LG_AI_Agent_Workshop.ipynb
├─ scripts/
│    └─ example_script.py
└─ data/
     └─ sample_data.csv

README.md : 워크숍 안내 및 실행 방법
requirements.txt : 실습에 필요한 Python 패키지 목록
.gitignore : Git에서 제외할 파일/폴더 정의
notebooks/ : Jupyter 실습 노트북 보관 폴더
scripts/ : 실습용 Python 스크립트
data/ : 예제 데이터 보관용 폴더


