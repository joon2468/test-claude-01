# Claude Code `/config` 설정 옵션 메모

> `/config` 명령으로 열리는 설정 인터페이스 옵션 정리.
> 설정 파일 위치: `~/.claude/settings.json` (유저), `.claude/settings.json` (프로젝트)

---

## 모델 & 실행

| 옵션 | 값 | 설명 |
|------|-----|------|
| `modelId` | 모델 ID 문자열 | 기본 모델 오버라이드 (예: `"claude-sonnet-4-6"`) |
| `availableModels` | 모델 이름 배열 | `/model`로 선택 가능한 모델 제한 |
| `effortLevel` | `"low"` / `"medium"` / `"high"` | 세션 간 노력 수준 유지 (Opus 4.6, Sonnet 4.6 지원) |
| `alwaysThinkingEnabled` | Boolean | 모든 세션에서 extended thinking 기본 활성화 |

---

## 세션 & 메모리

| 옵션 | 값 | 설명 |
|------|-----|------|
| `cleanupPeriodDays` | 숫자 (기본: 30) | 비활성 세션 삭제 기간. `0`이면 세션 저장 비활성화 |
| `autoMemoryDirectory` | 경로 문자열 | 자동 메모리 저장 디렉토리 커스텀 경로 |
| `plansDirectory` | 경로 문자열 | 플랜 파일 저장 디렉토리 (기본: `~/.claude/plans`) |

---

## UI & 표시

| 옵션 | 값 | 설명 |
|------|-----|------|
| `language` | 언어 코드 (예: `"japanese"`) | Claude 응답 언어 설정 |
| `showTurnDuration` | Boolean (기본: true) | 응답 후 소요 시간 표시 여부 |
| `spinnerVerbs` | 객체 | 스피너 동작 동사 커스텀 (`mode`: `"replace"` or `"append"`) |
| `spinnerTipsEnabled` | Boolean (기본: true) | 작업 중 스피너에 팁 표시 여부 |
| `terminalProgressBarEnabled` | Boolean (기본: true) | 터미널 진행 막대 활성화 |
| `prefersReducedMotion` | Boolean | UI 애니메이션 감소 (접근성) |

---

## Git & 기여

| 옵션 | 값 | 설명 |
|------|-----|------|
| `attribution` | `{commit, pr}` 객체 | 커밋/PR에 Claude 기여 문구 커스텀. 빈 문자열이면 숨김 |
| `includeGitInstructions` | Boolean (기본: true) | 커밋/PR 워크플로우 지침을 시스템 프롬프트에 포함 |

---

## 권한 & 보안

| 옵션 | 값 | 설명 |
|------|-----|------|
| `permissions.allow` | 규칙 문자열 배열 | 자동 허용할 도구 권한 규칙 (예: `["Bash(npm run test *)"]`) |
| `permissions.ask` | 규칙 문자열 배열 | 확인 요청할 도구 권한 규칙 |
| `permissions.deny` | 규칙 문자열 배열 | 거부할 도구 권한 규칙 |
| `permissions.additionalDirectories` | 경로 배열 | Claude가 접근 가능한 추가 작업 디렉토리 |
| `permissions.defaultMode` | `"askPerTool"` / `"acceptEdits"` / `"askForLargeChanges"` / `"bypassPermissions"` | 기본 권한 모드 |
| `permissions.disableBypassPermissionsMode` | `"disable"` | `bypassPermissions` 모드 비활성화 |

---

## 샌드박스

| 옵션 | 값 | 설명 |
|------|-----|------|
| `sandbox.enabled` | Boolean (기본: false) | bash 샌드박싱 활성화 (macOS, Linux, WSL2) |
| `sandbox.autoAllowBashIfSandboxed` | Boolean (기본: true) | 샌드박스 시 bash 자동 승인 |
| `sandbox.excludedCommands` | 명령어 배열 | 샌드박스 밖에서 실행할 명령어 목록 |
| `sandbox.filesystem.allowWrite` | 경로 배열 | 샌드박스에서 쓰기 허용할 추가 경로 |
| `sandbox.filesystem.denyWrite` | 경로 배열 | 샌드박스에서 쓰기 금지할 경로 |
| `sandbox.filesystem.denyRead` | 경로 배열 | 샌드박스에서 읽기 금지할 경로 |
| `sandbox.network.allowedDomains` | 도메인 패턴 배열 | 아웃바운드 트래픽 허용 도메인 (와일드카드 지원) |
| `sandbox.network.allowLocalBinding` | Boolean (macOS only) | localhost 포트 바인딩 허용 |

---

## MCP 서버

| 옵션 | 값 | 설명 |
|------|-----|------|
| `enableAllProjectMcpServers` | Boolean | 프로젝트 `.mcp.json`의 모든 MCP 서버 자동 승인 |
| `enabledMcpjsonServers` | 서버 이름 배열 | 승인할 특정 MCP 서버 목록 |
| `disabledMcpjsonServers` | 서버 이름 배열 | 거부할 특정 MCP 서버 목록 |

---

## 환경 & 인증

| 옵션 | 값 | 설명 |
|------|-----|------|
| `env` | 키-값 객체 | 모든 세션에 적용할 환경 변수 |
| `apiKeyHelper` | 경로 문자열 | API 키 생성 커스텀 스크립트 경로 |
| `autoUpdatesChannel` | `"stable"` / `"latest"` | 업데이트 채널 (`"stable"`은 약 1주일 지연) |
| `forceLoginMethod` | `"claudeai"` / `"console"` | 로그인 방식 제한 |

---

## 기타

| 옵션 | 값 | 설명 |
|------|-----|------|
| `outputStyle` | 스타일 이름 | 출력 스타일 설정 (시스템 프롬프트 조정) |
| `statusLine` | `{type, command}` 객체 | 커스텀 상태 표시줄 설정 |
| `hooks` | 훅 설정 객체 | 라이프사이클 이벤트에 실행할 커스텀 명령어 |
| `disableAllHooks` | Boolean | 모든 훅 비활성화 |
| `worktree.symlinkDirectories` | 디렉토리 배열 | 워크트리 간 심링크할 디렉토리 (예: `node_modules`) |
| `worktree.sparsePaths` | 경로 배열 | 워크트리에서 sparse-checkout할 디렉토리 |
| `feedbackSurveyRate` | 0–1 숫자 | 세션 품질 설문 노출 확률 |
| `teammateMode` | `"auto"` / `"in-process"` / `"tmux"` | 에이전트 팀원 표시 방식 |
| `fastModePerSessionOptIn` | Boolean | fast mode를 세션별 opt-in 방식으로 전환 |

---

## 설정 적용 범위 (우선순위 높은 순)

1. **Managed** — 시스템 관리 (`managed-settings.json`)
2. **Local** — 프로젝트 로컬 (`.claude/settings.local.json`, 비공유)
3. **Project** — 팀 공유 (`.claude/settings.json`)
4. **User** — 전체 프로젝트 공통 (`~/.claude/settings.json`)
