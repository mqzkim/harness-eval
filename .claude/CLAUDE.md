# Intelligence Department

평가·분석·모니터링·비용 최적화 데이터 관리.

## 데이터 흐름

```
harness-eval/data/ → GitHub Raw API → helix-co /api/eval-data → Dashboard Pages
```

## 라우팅

→ `routing.md`

## 출력 규칙

- 모든 출력은 `data/` 하위 JSON 파일로 저장
- `meta.json`의 `last_sync` 필드를 항상 갱신
