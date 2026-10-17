# Copilot Instructions (`space-quiz`)

## 응답 언어 및 말투 규칙

- 모든 답변은 **무조건 한국어**로 작성한당.
- 문장의 말끝을 `~다` 대신 **`~당`**으로 끝낸당 (예: `~한당`, `~했당`, `~인 거당`).

## 아키텍처 및 실행 환경

- **단일 파일 무의존성 구조**: 이 프로젝트는 별도의 빌드 도구, 서버, 외부 라이브러리 없이 `index.html` 파일 하나로 동작하는 한국어 우주 탐험 퀴즈 웹 앱입니다.
- **실행 및 검증 방법**:
  - 로컬 서버 없이 `file:///.../index.html` URL로 브라우저(또는 내장 브라우저 캔버스)에서 직접 열어 실행합니다.
  - UI 및 동작 검증은 내장 브라우저 캔버스의 `read_page`와 `evaluate_javascript` 액션을 사용해 질문 전환, 점수 반영, 피드백 클래스(`.correct`, `.wrong`), 키보드 포커스 이동을 확인합니다.

## 핵심 코드 규칙 및 패턴

- **상태 및 흐름 관리**:
  - `questions` 배열(10개 문항, `q`, `options`, `answer`, `explanation` 속성)을 기반으로 `currentIdx`, `score`, `answered` 전역 상태로 진행 상태를 관리합니다.
  - 중복 응답 방지를 위해 `selectOption()` 호출 시 `answered = true`로 설정하고 모든 `.option-btn`을 즉시 `disabled` 처리합니다.
- **키보드 접근성 및 포커스 제어**:
  - 보기 선택 직후 `#nextBtn`으로 포커스를 이동하고, 다음 문제 렌더링(`renderQuestion(true)`) 시 첫 번째 `.option-btn`으로, 결과 화면 전환(`showResults()`) 시 `#restartBtn`으로 포커스를 자동 이동시켜 포커스 유실을 방지합니다.
  - `keydown` 리스너를 통해 미응답 상태에서 방향키(`ArrowUp`/`ArrowDown`/`ArrowLeft`/`ArrowRight`) 포커스 순환과 숫자키(`1`~`4`) 즉시 선택이 동작해야 합니다.
- **스타일 및 애니메이션 규칙**:
  - `:root` CSS 변수와 `@media (prefers-color-scheme: dark)`를 통해 라이트/다크 모드를 자동 지원하므로, 색상 추가 및 수정 시 하드코딩 대신 CSS 변수를 사용합니다.
  - 중앙 정렬된 단일 컬럼(`.container`, `max-width: 480px`)과 본문 `15px` 산세리프 타이포그래피를 유지합니다.
  - 정답 선택 시 초록색 펄스(`.correct` / `correctPulse`)와 점수 배지 팝업(`.bump` / `scorePop`), 오답 선택 시 빨간색 흔들림(`.wrong` / `wrongShake`) 애니메이션 피드백을 유지합니다.
