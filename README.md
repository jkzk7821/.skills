# Loop Design Prompt

장기 Codex 목표를 설계하고 승인된 목표 지침을 간결한 `/goal` 프롬프트로 변환하는 플러그인입니다.

## Codex 설치

```bash
codex plugin marketplace add jkzk7821/.skills --ref feat/loop-design-prompt-codex-plugin
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

/loop-design-prompt:goal-plan
/loop-design-prompt:execute
```

설치가 끝나면 새 Codex 또는 Claude Code 세션을 시작해 스킬을 사용하세요.
