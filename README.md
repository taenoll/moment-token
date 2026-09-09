# Moment Token

현대적인 웹 애플리케이션을 위한 디자인 토큰 패키지입니다. CSS 변수, SCSS 변수, Tailwind 테마 토큰, 그리고 디자인 시스템 전반에서 일관된 스타일을 유지할 수 있도록 정리된 원본 JSON 토큰을 함께 제공합니다.

## 주요 기능

- 색상, 간격, radius, 타이포그래피용 CSS 커스텀 프로퍼티
- Sass 프로젝트용 SCSS 변수
- Tailwind v4 테마 지원
- 커스텀 도구나 문서 파이프라인에서 사용 가능한 원본 JSON 토큰
- npm 배포를 위해 자동 생성된 결과물 제공

## 설치

```bash
npm install @youjeong/moment-token
```

## 사용 방법

### CSS

```css
@import '@youjeong/moment-token/css';

.card {
  background: var(--color-surface-default);
  color: var(--color-text-primary);
  padding: var(--spacing-4);
  border-radius: var(--radius-md);
  border: 1px solid var(--color-border-subtle);
}
```

### SCSS

```scss
@use '@youjeong/moment-token/scss' as *;

.card {
  background: $color-surface-default;
  color: $color-text-primary;
  padding: $spacing-4;
  border-radius: $radius-md;
}
```

### Tailwind

```css
@import '@youjeong/moment-token/tailwind';
```

Tailwind v4의 `@theme` 네임스페이스에 테마 변수가 등록되므로, 유틸리티 클래스 안에서 디자인 토큰을 직접 사용할 수 있습니다.

## 제공되는 토큰 export

이 패키지는 다음 경로를 제공합니다.

- `@youjeong/moment-token/css` → CSS 커스텀 프로퍼티
- `@youjeong/moment-token/scss` → SCSS 변수
- `@youjeong/moment-token/tailwind` → Tailwind 테마 CSS
- `@youjeong/moment-token/tokens/*` → 원본 JSON 토큰 파일

## 포함된 토큰 그룹

- Colors
- Spacing
- Radius
- Typography

## 개발

```bash
npm install
npm run build
```

## 라이선스

MIT
