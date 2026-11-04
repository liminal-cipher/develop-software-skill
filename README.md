# develop-software

> AI 코딩 에이전트와 함께 소프트웨어를 설계·구현·검증하고, 작업 상태를 정확하게 인계하기 위한 Agent Skill.

## 어떤 Skill인가?

개발 작업을 다음 8단계로 진행하도록 돕는 지침이다.

1. 목표·범위·권한 확인
2. 현재 코드·환경 조사
3. 작업 규모에 맞춘 계획
4. 구현과 오류 원인 진단
5. 실제 실행·예외·회귀 검증
6. 사용자 직접 검토 지원
7. 현재 상태 기록 및 핸드오프
8. 구현 결과·검증 근거·한계 보고

## 프로젝트 Phase 운영

여러 구현 단계가 필요한 프로젝트에서는 `PLAN.md`에 Phase별 목표·산출물·
완료 기준·검증 방법을 기록한다. 첫 E2E를 확인한 뒤 필수 요구사항과 다시 대조하고,
각 Phase 종료 시 실제 검증·미확인·설명할 핵심 결정을 짧게 확인한다.
`CURRENT_TASK.md`에는 현재 Phase와 남은 작업만 유지한다.
각 Phase마다 새 문서나 사용자 승인을 강제하지 않으며, 미검증을 완료로 표시하지 않는다.

## 문제 해결과 이해 확인

다단계 작업에서는 **문제 상황과 목표를 정의하고, 제공된 자료에서 필수 조건을 먼저 추출**한다. 예외·경계·복합 조건을 함께 확인하고 요구사항을 수용 기준, 실제 구현 위치, 실행한 검사와 결과에 연결한다. 시험식 점수나 별도 평가 문서를 만들지 않고, 해결 결과가 원래 문제·제약에 적합한지도 점검한다.

중요한 설계는 문제 상황부터 시작해 작은 입력의 처리 과정과 선택 이유, 코드·테스트 근거, 실패 조건과 한계를 짧게 연결한다. 입력이 모듈 사이에서 어떻게 바뀌어 결과가 되는지도 실제 경로로 설명한다. 중요한 AI 제안을 채택·수정·거절·보류했다면 확인된 이유와 판단 주체를 남긴다.

각 주요 Phase에서 핵심 선택을 하거나 작업을 마칠 때 설명한 범위와 남은 이해 사항을 짧게 확인한다. **AI가 설명한 것과 사용자가 직접 이해를 확인한 것은 구분**한다. 사용자가 원하면 자기 말로 설명해 볼 수 있지만 답변을 기다리느라 개발을 멈추거나 퀴즈·추가 문서를 강제하지 않는다.

## 문서 구성과 맥락 관리

작고 명확한 작업에는 문서를 강제하지 않는다. 다단계 프로젝트에서는 **현재 상태를 짧게 유지하고 필요할 때만 상세 자료를 읽는다.**

| 문서 | 역할 | 생성 기준 |
| --- | --- | --- |
| `CURRENT_TASK.md` | 현재 작업·실제 검증 근거·다음 행동 1~3개. 핸드오프의 진입점 | 다단계 작업 |
| `PLAN.md` | 목표·범위·수용 기준·구현 및 검증 계획 | 의미 있는 계획이 필요한 작업 |
| `DECISIONS.md` | 중요한 기술·알고리즘 선택 이유·대안·가정·한계 | 주요 결정이 누적될 때 |
| `WORK_LOG.md` | 오래된 완료 단계·장애 해결 이력 | 별도 보존이 필요할 때만 선택 |

`PLAN.md`는 중요한 계획 변경과 Phase별 구현·검증 근거 연결 시 갱신하고, `CURRENT_TASK.md`는 주요 마일스톤에 현재 사실만 반영한다. 완료 이력을 무한히 누적하거나 제공된 요구사항을 반복 복사하지 않는다. 새 세션에서는 `CURRENT_TASK.md`부터 읽고 관련 문서의 필요한 부분과 실제 파일·검사를 대조한다. `WORK_LOG.md` 전체를 기본으로 다시 읽지 않는다.

사용자와는 기본적으로 한국어 반말로 대화하고, 작업 문서는 차분하고 자연스러운 한국어 문서체로 작성한다. 개발 설명은 **사용자가 보게 되는 동작과 결과부터** 말한 뒤 처리 과정·선택 이유·필요한 기술 명칭을 덧붙인다. 어색한 직역과 추상적인 수식어를 줄이되, 수치·조건·검증 상태와 코드 식별자는 정확히 유지한다. 기존 문서를 이해하기 쉽게 쓰는 것이 우선이며 별도 윤문 Skill이나 긴 용어집은 필요하지 않다. 별도 Subagent, 외부 모델, MCP 또는 설치 스크립트는 필수가 아니다.

## 구성

- `SKILL.md`: 에이전트가 개발 작업에 적용할 핵심 지침
- `README.md`: 저장소의 목적, 설치 방식과 검증 방법을 설명하는 문서
- `templates/`: 필요할 때 선택해 사용할 한국어 문서 양식

## 프로젝트에 설치하기

플랫폼에서 공개 Git 저장소 사용이 허용된 경우의 예시다. 프로젝트 루트를 확인한 뒤 해당 위치에서 실행한다.

```bash
pwd
git clone --depth 1 https://github.com/liminal-cipher/develop-software-skill.git /tmp/develop-software-skill
mkdir -p .agents/skills/develop-software
cp /tmp/develop-software-skill/SKILL.md .agents/skills/develop-software/SKILL.md
cp -R /tmp/develop-software-skill/templates .agents/skills/develop-software/templates
```

설치 경로와 자동 발견 동작은 사용 중인 Codex 버전·설정에 따라 확인한다. Skill이 자동으로 인식되지 않으면 현재 프로젝트의 `SKILL.md`를 명시적으로 읽고 적용하도록 요청할 수 있다. Codex 버전이나 전역 설정을 변경할 필요는 없다.


Windows PowerShell 설치 예시:

~~~powershell
$skillSource = Join-Path $env:TEMP "develop-software-skill"
$skillTarget = ".agents/skills/develop-software"

git clone --depth 1 https://github.com/liminal-cipher/develop-software-skill.git $skillSource
New-Item -ItemType Directory -Force $skillTarget | Out-Null
Copy-Item (Join-Path $skillSource "SKILL.md") (Join-Path $skillTarget "SKILL.md")
New-Item -ItemType Directory -Force (Join-Path $skillTarget "templates") | Out-Null
Copy-Item -Path (Join-Path $skillSource "templates/*") -Destination (Join-Path $skillTarget "templates") -Recurse -Force
~~~

기존 템플릿을 직접 수정해 사용 중이라면 덮어쓰기 전에 변경 내용을 보존한다. 템플릿은 선택 사항이며 프로젝트에 필요한 문서만 만든다.

## 확인할 동작

- 설계·리뷰 요청만 받았을 때 임의로 구현을 시작하지 않는가?
- 긴 요구사항의 정상·예외·복합 조건과 출처를 `PLAN.md`에서 완료 기준·구현 위치·실제 검사 결과와 연결하고, 첫 E2E와 주요 Phase 뒤 빠진 필수 조건을 다시 확인하는가?
- 다단계 작업에서 Phase별 목표·완료 기준·검증 상태를 구분하고, 중요한 미확인을 다음 Phase에 숨기지 않는가?
- 중요한 알고리즘·아키텍처 선택을 작은 예시, 대안, 보장 범위와 한계로 설명하는가?
- Subagent 작업에 명확한 파일 범위·완료 기준·검증 근거가 있고, 메인 에이전트가 통합 검사를 하는가?
- 0건 실행·전체 skip을 PASS로 오인하지 않고, 핵심 계산을 독립된 방법으로 대조하는가?
- 주요 마일스톤에서 실제 동작을 쉬운 한국어로 설명하고, AI의 작업과 사용자의 실제 판단·확인, 이해되지 않은 부분을 구분하는가?
- 대표 입력이 모듈 사이에서 어떻게 변환되어 결과가 되는지와 중요한 실패 경로를 실제 코드로 설명하는가?
- 중요한 AI 제안의 채택·수정·거절·보류 이유와 판단 주체를 확인된 근거로만 남기는가?
- 주요 Phase에서 필요한 설명을 먼저 제공하고, 남은 이해 사항을 확인하되 퀴즈나 답변 대기를 강제하지 않는가?
- `PLAN.md`·`DECISIONS.md`의 추상적인 표현을 구체적 동작으로 설명하면서 수치·조건·기술 명칭은 유지하는가?
- 새 세션에서는 짧은 상태 문서와 필요한 참조만 읽고 실제 파일·검사 결과를 대조하는가?

## 상태와 사용 조건

이 저장소는 공개 테스트용 개발 지침이다. 실제 Codex 환경에서 자동 발견·동작 검증은 아직 완료되지 않았다. 사용 환경의 지침과 제한을 우선하고, 비공개 자료·자격증명·제삼자의 과제 결과물을 저장소에 포함하지 않는다.
