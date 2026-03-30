---
name: eval-sync
description: Supabase DB에서 평가·분석·모니터링·비용 데이터를 추출하여 data/ 하위 JSON으로 동기화하고 harness-eval 레포에 커밋한다. evaluation, analytics, monitor, cost 요청 시 사용한다.
user-invocable: true
argument-hint: "[evaluations|analytics|monitor|cost|all]"
allowed-tools: Read, Write, Edit, Bash, Glob, Grep
---

# Eval Sync

helix-co Supabase DB → harness-eval/data/ JSON 동기화.

## 실행 절차

### Step 1: 대상 파악

`$ARGUMENTS`에서 동기화 대상을 파악한다.
인수 없으면 → `all` 로 처리한다.

### Step 2: 데이터 추출

| 대상 | Supabase 테이블 | 출력 파일 |
|------|----------------|----------|
| evaluations | evaluations, benchmarks | data/evaluations.json |
| analytics | sessions, events, dailyStats | data/analytics.json |
| monitor | dispatchStatus, pipelineRuns | data/monitor.json |
| cost | sessions (costUsd, tokensUsed) | data/cost.json |

### Step 3: JSON 생성

각 출력 파일의 `summary` 섹션을 집계한다.
`data/meta.json`의 `last_sync`를 현재 시간으로 갱신한다.

### Step 4: 커밋·푸시

```bash
git add data/
git commit -m "sync: <대상> 동기화 (<날짜>)"
git push origin main
```
