# 🚀 우주 탐험 퀴즈 (Space Quiz)

인류의 우주 탐사 역사와 주요 탐사선, 대한민국의 우주 개발 성과를 주제로 한 10문항 한국어 인터랙티브 퀴즈 웹 앱입니다. 별도의 빌드 도구나 외부 라이브러리 없이 단일 `index.html` 파일만으로 동작합니다.

## ✨ 주요 기능

- **10개의 우주 탐사 퀴즈**: 유리 가가린, 아폴로 11호, 보이저 1호, 누리호, 다누리, 제임스 웹 우주망원경 등 핵심 우주 탐사 상식을 다룹니다.
- **즉각적인 시각 피드백**: 정답/오답 선택 시 애니메이션 효과와 함께 상세 해설을 제공합니다.
- **키보드 접근성 지원**: 방향키(`↑`/`↓`/`←`/`→`)로 보기 간 포커스를 이동하고, 숫자키(`1`~`4`)로 보기를 바로 선택할 수 있습니다.
- **라이트/다크 모드 자동 전환**: 시스템 색상 설정(`prefers-color-scheme`)에 맞춰 테마가 자동으로 적용됩니다.

## 🖥️ 로컬 실행 방법

별도의 패키지 설치나 빌드 과정이 필요하지 않습니다.

### 방법 1: 브라우저에서 직접 열기
리포지토리를 클론한 뒤 `index.html` 파일을 브라우저에서 바로 엽니다.

```bash
git clone https://github.com/Requle26/space-quiz.git
cd space-quiz
open index.html # macOS (Windows의 경우 start index.html)
```

### 방법 2: 로컬 정적 서버로 실행하기 (선택 사항)
Python 등이 설치되어 있다면 간단한 로컬 웹 서버로 실행할 수도 있습니다.

```bash
python3 -m http.server 8000
```
이후 브라우저에서 `http://localhost:8000`으로 접속합니다.

## 🌐 배포

`main` 브랜치에 변경 사항이 푸시되면 GitHub Actions 워크플로(`.github/workflows/deploy.yml`)를 통해 GitHub Pages로 자동 배포됩니다.
- 배포 URL: [https://requle26.github.io/space-quiz/](https://requle26.github.io/space-quiz/)
