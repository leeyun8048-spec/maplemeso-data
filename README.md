# maplemeso-data

메이플메소(MapleMeso) 앱이 읽는 보스 결정석 가격표입니다.
앱은 실행할 때 이 파일을 받아 가격을 맞추고, 받지 못하면 앱에 들어 있는 가격표를 씁니다.

- `v1/kms.json`: 한국 서버
- `v1/gms.json`: 글로벌 서버

## 고치는 방법
1. 파일을 열고 연필(Edit) 버튼을 누릅니다.
2. 숫자를 고치거나 보스 한 줄을 추가합니다.
3. `updatedAt`을 오늘 날짜(YYYY-MM-DD)로 바꿉니다.
4. Commit changes를 누릅니다.

앱은 6시간에 한 번 새 파일을 확인합니다. 설정 → 서버 → [새로 확인]을 누르면 바로 확인합니다.

## 규칙 (지키지 않으면 앱이 파일 전체를 무시하고 기존 가격표를 씁니다)
- 가격은 따옴표 없는 정수입니다. 예: `48900000` (O) / `"48,900,000"` (X)
- `difficulties`에 적은 난이도는 `crystalPrices`에도 모두 있어야 합니다.
- 난이도: `easy`, `normal`, `hard`, `chaos`, `extreme`
- 분류(category): `weekly`(주간), `monthly`(월간), `season`(시즌)
- 가격 숫자는 그대로 반영되니 0 개수를 꼭 확인하세요.
- **보스 줄을 지우지 마세요.** 지워도 앱은 기존 보스를 유지합니다. 더 이상 안 쓰는 보스는 `"retired": true`를 붙이면 목록에서 사라집니다. (이미 등록한 캐릭터에서만 보이고 뺄 수 있음)
- 보스 이름이 바뀌면 새 이름으로 바꾸고 `"aliases": ["예전 이름"]`을 붙입니다. 기존 기록과 이어집니다.
- `schemaVersion`은 바꾸지 마세요.

## 예시
```json
{"name": "새보스", "category": "weekly", "difficulties": ["normal", "hard"], "crystalPrices": {"normal": 1500000000, "hard": 4000000000}}
{"name": "새시즌보스", "category": "season", "difficulties": ["normal"], "crystalPrices": {"normal": 300000000}, "rewardLabel": "메소 주머니"}
```
