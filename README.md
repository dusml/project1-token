# project1-token

프로젝트에서 공통으로 사용하는 디자인 토큰을 CSS, SCSS, Tailwind CSS 형식으로
생성하는 npm 패키지입니다. 토큰 원본은 `tokens/` 디렉터리의 JSON 파일로
관리하며, Style Dictionary를 사용해 배포용 스타일 파일을 생성합니다.

## 설치

```bash
npm install project1-token
```

## 사용 방법

### CSS

```css
@import "project1-token/dist/css/variables.css";
```

생성된 CSS 변수는 `var()`로 사용할 수 있습니다.

```css
.button {
  color: var(--color-text-black);
  background-color: var(--color-brand-primary);
  padding: var(--spacing-4);
  border-radius: var(--radius-md);
  font-size: var(--font-size-body);
}
```

### SCSS

```scss
@use "project1-token/dist/scss/variables" as tokens;

.button {
  color: tokens.$color-text-black;
  background-color: tokens.$color-brand-primary;
  padding: tokens.$spacing-4;
  border-radius: tokens.$radius-md;
}
```

### Tailwind CSS

Tailwind CSS v4를 사용하는 경우 `@theme` 파일을 프로젝트의 CSS에
불러올 수 있습니다.

```css
@import "project1-token/dist/tailwind/theme.css";
```

## 제공 토큰

| 분류 | 예시 |
| --- | --- |
| 색상 | `--color-brand-primary`, `--color-text-black` |
| 간격 | `--spacing-1` ~ `--spacing-10` |
| 모서리 반경 | `--radius-sm`, `--radius-md`, `--radius-lg`, `--radius-xl`, `--radius-full` |
| 글꼴 크기 | `--font-size-display`, `--font-size-h1`, `--font-size-body` |
| 행간 | `--leading-tight`, `--leading-normal` |
| 자간 | `--tracking-tight`, `--tracking-normal`, `--tracking-wide` |
| 글꼴 | `--font-primary`, `--font-display` |

색상은 primitive 토큰과 semantic 토큰으로 나뉘며, semantic 토큰은
primitive 토큰을 참조합니다. 따라서 컴포넌트에서는 가능한 semantic 토큰을
사용하는 것을 권장합니다.

## 개발 및 토큰 빌드

의존성을 설치한 뒤 다음 명령어로 모든 플랫폼의 파일을 생성합니다.

```bash
npm install
npm run build
```

생성되는 파일은 다음과 같습니다.

```text
dist/
├── css/variables.css
├── scss/_variables.scss
└── tailwind/theme.css
```

새 토큰을 추가하거나 기존 토큰을 수정하려면 `tokens/` 아래의 JSON 파일을
변경한 후 `npm run build`를 다시 실행하세요.

## 패키지 배포

새 버전을 배포하기 전에 빌드와 패키지 포함 파일을 확인하세요.

```bash
npm run build
npm pack --dry-run
npm publish
```

## 라이선스

ISC
