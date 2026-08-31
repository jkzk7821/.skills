# Loop Design Prompt

장기 에이전트 목표를 설계하고 승인된 목표 지침을 간결한 `/goal` 프롬프트로 변환하는 플러그인입니다.
Codex와 Claude Code 모두 `/goal`을 제공하므로 같은 계약을 양쪽에서 그대로 발사할 수 있습니다.

## Codex 설치

```bash
codex plugin marketplace add jkzk7821/.skills --ref loop-design-prompt
codex plugin add loop-design-prompt@jkzk7821-skills
```

## Claude Code 설치

```text
/plugin marketplace add jkzk7821/.skills
/plugin install loop-design-prompt@jkzk7821-skills
```

## 사용 가능한 스킬

```text
$loop-design-prompt:goal-plan
$loop-design-prompt:execute
$loop-design-prompt:loop-design-prompt

/loop-design-prompt:goal-plan
/loop-design-prompt:execute
/loop-design-prompt:loop-design-prompt
```

`goal-plan`과 `execute`는 파이프라인입니다. 요청을 그것이 받을 자격이 있는 프롬프트로
빚어내고(`goal-plan`), 그 인라인 맥락을 검토한 뒤 발사합니다(`execute`).

`loop-design-prompt`는 같은 판단을 한 스킬에 담은 독립본입니다. 계약을 쓰는 일과
이미 있는 목표·루프를 점검하는 일을 한 자리에서 처리합니다.

설치가 끝나면 새 Codex 또는 Claude Code 세션을 시작해 스킬을 사용하세요.
