# harness-eval

Intelligence 부서 데이터 저장소 — 평가, 분석, 모니터링, 비용 최적화.

## 구조

```
harness-eval/
├── .claude/             # harness-infra 기반
├── data/
│   ├── meta.json        # 부서 메타
│   ├── evaluations.json # D/ND 평가 결과
│   ├── analytics.json   # 세션·도구·작업 분석
│   ├── monitor.json     # 실시간 모니터링 상태
│   └── cost.json        # 비용 분석·최적화
└── config/
    └── department.json
```

## helix-co 대시보드 페이지

| 페이지 | 경로 | 데이터 파일 |
|--------|------|-----------|
| Evaluations | /eval | evaluations.json |
| Analytics | /analytics | analytics.json |
| Monitor | /monitor | monitor.json |
| Cost Optimizer | /cost-optimizer | cost.json |
