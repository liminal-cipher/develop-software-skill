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

시간 제한이 있는 작업에서는 시작할 때 종료 시각과 기능 동결 시각을 `CURRENT_TASK.md`에 적는다. 질문과 계획에는 상한을 두고(따로 정하지 않았으면 둘을 합쳐 전체 시간의 약 10%), 핵심 로직을 다듬기 전에 샘플 데이터로라도 입력부터 결과까지 도는 첫 E2E를 먼저 만든다. 동결 시각 이후에는 새 기능, 모델·설정 변경을 하지 않고 검증·정리·한계 기록만 한다.

## 문제 해결과 이해 확인

다단계 작업에서는 **문제 상황과 목표를 정의하고, 제공된 자료에서 필수 조건을 먼저 추출**한다. 예외·경계·복합 조건을 함께 확인하고 요구사항을 수용 기준, 실제 구현 위치, 실행한 검사와 결과에 연결한다. 시험식 점수나 별도 평가 문서를 만들지 않고, 해결 결과가 원래 문제·제약에 적합한지도 점검한다.

복잡한 설계는 채택하기 전에 **왜 필요한가 → 가장 단순한 작동 예 → 입력에서 출력까지 → 제약을 충족하는 방식 → 대안과 한계** 순서로 설명한다. 측정하지 않은 최적성·성능은 보장으로 주장하지 않고 향후 개선으로 분리한다. 중요한 AI 제안을 채택·수정·거절·보류했다면 확인된 이유와 판단 주체를 남긴다.

다단계 작업에서는 Phase를 마칠 때와 최종 보고 전에 **모든 필수 요구사항을 PASS / FAIL / NOT RUN 표로 출력**한다. FAIL이나 NOT RUN이 남은 요구사항은 완료로 보고하지 않는다. 단일 단계의 작은 작업은 검사 결과를 문장으로 보고해도 된다.

첫 E2E 결과, 주요 Phase 종료, 최종 보고 때는 핵심 모듈, 데이터 흐름, AI 제안의 채택·기각, 검증 근거, 가정과 한계를 1~2분 안에 읽을 수 있게 요약한다. **AI가 설명한 것과 사용자가 직접 이해를 확인한 것은 구분**한다. 사용자가 원하면 자기 말로 설명해 볼 수 있지만, 답변을 기다리느라 개발을 멈추거나 퀴즈·추가 문서를 강제하지 않는다.

## 문서 구성과 맥락 관리

작고 명확한 작업에는 문서를 강제하지 않는다. 다단계 프로젝트에서는 **현재 상태를 짧게 유지하고 필요할 때만 상세 자료를 읽는다.**

| 문서 | 역할 | 생성 기준 |
| --- | --- | --- |
| `CURRENT_TASK.md` | 현재 작업·실제 검증 근거·다음 행동 1~3개. 핸드오프의 진입점 | 다단계 작업 |
| `PLAN.md` | 목표·범위·수용 기준·구현 및 검증 계획 | 의미 있는 계획이 필요한 작업 |
| `DECISIONS.md` | 중요한 기술·알고리즘 선택 이유·대안·가정·한계 | 주요 결정이 누적될 때 |
| `WORK_LOG.md` | 오래된 완료 단계·장애 해결 이력 | 별도 보존이 필요할 때만 선택 |

`PLAN.md`는 중요한 계획 변경과 Phase별 구현·검증 근거 연결 시 갱신하고, `CURRENT_TASK.md`는 주요 마일스톤에 현재 사실만 반영한다. 완료 이력을 무한히 누적하거나 제공된 요구사항을 반복 복사하지 않는다. 새 세션이나 자동 compact 뒤에는 `CURRENT_TASK.md`부터 읽고, 작업을 이어가기 전에 `git status`·`git diff` 또는 실제 파일·검사 결과와 대조한다. 문서와 파일이 다르면 파일을 기준으로 문서를 고친다. `WORK_LOG.md` 전체를 기본으로 다시 읽지 않는다.

사용자와는 기본적으로 한국어 반말로 대화하고, 작업 문서는 차분하고 자연스러운 한국어 문서체로 작성한다. 개발 설명은 **사용자가 보게 되는 동작과 결과부터** 말한 뒤 처리 과정·선택 이유·필요한 기술 명칭을 덧붙인다. 어색한 직역과 추상적인 수식어를 줄이되, 수치·조건·검증 상태와 코드 식별자는 정확히 유지한다. 기존 문서를 이해하기 쉽게 쓰는 것이 우선이며 별도 윤문 Skill이나 긴 용어집은 필요하지 않다. 별도 Subagent, 외부 모델, MCP 또는 설치 스크립트는 필수가 아니다.

## 구성

- `SKILL.md`: 에이전트가 개발 작업에 적용할 핵심 지침
- `README.md`: 저장소의 목적, 설치 방식과 검증 방법을 설명하는 문서
- `templates/`: 필요할 때 선택해 사용할 한국어 문서 양식. `templates/AGENTS.md`는 프로젝트 루트에 두는 짧은 진입 지침이다.

이 저장소가 `develop-software`의 원본이다. 다른 저장소에 별도 편집본을 두지 않고,
설치본은 이 저장소의 선택한 버전에서 가져온다. 스킬을 수정할 때는 원본 저장소에서
수정·검증한 뒤 게시하고, 사용하는 환경의 설치본을 갱신한다.

## 프로젝트에 설치하기

플랫폼에서 공개 Git 저장소 사용이 허용된 경우의 최초 설치 예시다. 프로젝트 루트를
확인한 뒤 해당 위치에서 실행한다. 원본은 프로젝트 옆의 `develop-software-skill`
폴더에 보관한다. 이미 원본을 복제했다면 다시 복제하지 않고 그 경로를 사용한다.
기존 설치본이 있으면 직접 변경한 내용부터 원본과 비교하고 보존한 뒤 갱신한다.

```bash
pwd
test ! -e .agents/skills/develop-software || exit 1
git clone --depth 1 https://github.com/liminal-cipher/develop-software-skill.git ../develop-software-skill || exit 1
mkdir -p .agents/skills/develop-software
cp ../develop-software-skill/SKILL.md .agents/skills/develop-software/SKILL.md
cp -R ../develop-software-skill/templates .agents/skills/develop-software/templates
test -e AGENTS.md || cp ../develop-software-skill/templates/AGENTS.md AGENTS.md
```

특정 버전을 고정해 사용하려면 `git clone` 명령에 `--branch <태그>`를 추가한다. 예를 들어 `git clone --depth 1 --branch <태그> https://github.com/liminal-cipher/develop-software-skill.git ../develop-software-skill`처럼 쓴다.

설치 경로와 자동 발견 동작은 사용 중인 Codex 버전·설정에 따라 확인한다. Codex 버전이나 전역 설정을 변경할 필요는 없다. 프로젝트 루트의 `AGENTS.md`는 Skill이 자동으로 인식되지 않을 때도 핵심 규칙과 `SKILL.md` 경로를 전달하는 진입점이다. 위 명령은 `AGENTS.md`가 없을 때만 복사한다. 이미 있으면 덮어쓰지 말고 `templates/AGENTS.md`의 내용을 기존 파일 끝에 직접 추가한다.


Windows PowerShell 설치 예시:

~~~powershell
$skillSource = "../develop-software-skill"
$skillTarget = ".agents/skills/develop-software"

if (Test-Path -LiteralPath $skillTarget) { throw "기존 설치본의 변경 내용을 먼저 확인한다." }
git clone --depth 1 https://github.com/liminal-cipher/develop-software-skill.git $skillSource
if ($LASTEXITCODE -ne 0) { throw "원본 저장소를 복제하지 못했다." }
New-Item -ItemType Directory -Force $skillTarget | Out-Null
Copy-Item (Join-Path $skillSource "SKILL.md") (Join-Path $skillTarget "SKILL.md")
New-Item -ItemType Directory -Force (Join-Path $skillTarget "templates") | Out-Null
Copy-Item -Path (Join-Path $skillSource "templates/*") -Destination (Join-Path $skillTarget "templates") -Recurse -Force
if (-not (Test-Path -LiteralPath "AGENTS.md")) { Copy-Item (Join-Path $skillSource "templates/AGENTS.md") "AGENTS.md" }
~~~

기존 템플릿을 직접 수정해 사용 중이라면 덮어쓰기 전에 변경 내용을 보존한다. 템플릿은 선택 사항이며 프로젝트에 필요한 문서만 만든다.

## 확인할 동작

- 설계·리뷰 요청만 받았을 때 임의로 구현을 시작하지 않는가?
- 긴 요구사항의 정상·예외·복합 조건과 출처를 `PLAN.md`에서 완료 기준·구현 위치·실제 검사 결과와 연결하고, 첫 E2E와 주요 Phase 뒤 빠진 필수 조건을 다시 확인하는가?
- 다단계 작업에서 Phase별 목표·완료 기준·검증 상태를 구분하고, 중요한 미확인을 다음 Phase에 숨기지 않는가?
- 중요한 알고리즘·아키텍처 선택을 필요성 → 작은 예시 → 입력에서 출력까지 → 제약 충족 → 대안과 한계 순서로 설명하는가?
- 다단계 작업의 Phase 종료와 최종 보고에서 모든 필수 요구사항을 PASS / FAIL / NOT RUN 표로 출력하고, 측정하지 않은 최적성을 향후 개선으로 분리하는가?
- Subagent 작업에 명확한 파일 범위·완료 기준·검증 근거가 있고, 메인 에이전트가 통합 검사를 하는가?
- 0건 실행·전체 skip을 PASS로 오인하지 않고, 핵심 계산을 독립된 방법으로 대조하는가?
- 주요 마일스톤에서 실제 동작을 쉬운 한국어로 설명하고, AI의 작업과 사용자의 실제 판단·확인, 이해되지 않은 부분을 구분하는가?
- 대표 입력이 모듈 사이에서 어떻게 변환되어 결과가 되는지와 중요한 실패 경로를 실제 코드로 설명하는가?
- 중요한 AI 제안의 채택·수정·거절·보류 이유와 판단 주체를 확인된 근거로만 남기는가?
- 주요 Phase에서 필요한 설명을 먼저 제공하고, 남은 이해 사항을 확인하되 퀴즈나 답변 대기를 강제하지 않는가?
- `PLAN.md`·`DECISIONS.md`의 추상적인 표현을 구체적 동작으로 설명하면서 수치·조건·기술 명칭은 유지하는가?
- 새 세션이나 자동 compact 뒤에 짧은 상태 문서와 필요한 참조만 읽고, `git status`·`git diff` 또는 실제 파일·검사 결과와 대조하는가?
- 시간 제한 작업에서 종료·동결 시각을 기록하고, 질문·계획 상한과 첫 E2E 우선을 지키며, 동결 이후 새 기능이나 모델 변경을 하지 않는가?

## 상태와 사용 조건

이 저장소는 공개 테스트용 개발 지침이다. 실제 Codex 환경에서 자동 발견·동작 검증은 아직 완료되지 않았다. 사용 환경의 지침과 제한을 우선하고, 비공개 자료·자격증명·제삼자의 과제 결과물을 저장소에 포함하지 않는다.
