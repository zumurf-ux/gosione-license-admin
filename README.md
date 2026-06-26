# 고시ONE / 인건비서 라이선스 관리페이지

이 버전의 `확인` 버튼은 관리페이지에서 업데이트 팝업을 띄우지 않습니다.

동작 흐름:

1. 관리자가 관리페이지에서 등록 기기의 `확인` 버튼을 누릅니다.
2. 서버에 해당 라이선스의 `manual_check_requested_at` 값이 저장됩니다.
3. 등록된 기기 앱이 기존 라이선스 확인을 실행할 때 서버 응답에서 `manual_check_requested: true`를 받습니다.
4. 기기 앱은 라이선스 확인과 업데이트 확인을 실행합니다.
5. 앱 버전이 낮으면 기기 화면에 업데이트 팝업이 표시됩니다.

주의:

- 관리페이지 버튼만으로 이미 설치된 기기에 즉시 팝업을 밀어 넣는 방식은 아닙니다.
- 기기 앱이 서버를 확인해야 요청을 받을 수 있습니다.
- 기존 24시간 자동 확인은 그대로 유지되고, 관리페이지 `확인` 버튼은 같은 확인을 수동으로 요청하는 역할입니다.

포함 파일:

- `index.html`: GitHub Pages에 올릴 관리페이지
- `supabase-manual-device-check.sql`: Supabase 테이블에 필요한 컬럼 추가 SQL
- `supabase/functions/license-admin-request-device-check-patch.js`: `license-admin` 함수에 추가할 요청 저장 코드
- `supabase/functions/license-verify-manual-check-patch.js`: `license-verify` 함수에 반영할 기기 응답 코드
