# Moment Token

Moment Token은 디자인 시스템에서 일관된 스타일을 빠르고 안정적으로 제공하기 위한 디자인 토큰 패키지입니다. CSS 커스텀 프로퍼티, SCSS 변수, Tailwind 테마, 원본 JSON 토큰을 함께 제공하여 다양한 프론트엔드 워크플로우에서 쉽게 사용할 수 있도록 설계되었습니다.

주요 사용 사례:

- 디자인 시스템(Design System)에서 토큰을 중앙 관리
- 프로젝트별 빌드 파이프라인에 토큰을 간편하게 통합
- CSS/SCSS/Tailwind 등 다양한 환경에서 동일한 시각적 결과 보장

---

## 주요 특징

- 색상, 간격(spacing), 반경(radius), 타이포그래피(폰트/라인높이) 등 필수 토큰 제공
- CSS 커스텀 프로퍼티(.css) 및 SCSS 변수(.scss) 지원
- Tailwind v4 테마로의 손쉬운 통합 지원
- 원본 JSON 토큰(tokesn/*.json) 제공으로 자체 도구나 문서화 파이프라인에 활용 가능
- npm 배포용으로 빌드된 결과물 포함

---

## 설치

```bash
npm install @youjeong/moment-token
```

> 프로젝트에 스코프가 다른 패키지 이름을 사용 중이라면 위 이름을 실제 패키지명으로 변경하세요.

---

## 빠른 시작

### 1) CSS (브라우저에서 CSS 변수로 사용)

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

### 2) SCSS (Sass 프로젝트)

```scss
@use '@youjeong/moment-token/scss' as *;

.card {
  background: $color-surface-default;
  color: $color-text-primary;
  padding: $spacing-4;
  border-radius: $radius-md;
}
```

### 3) Tailwind 통합

Tailwind 설정에서 Moment Token이 제공하는 테마를 불러와 사용합니다.

```js
// tailwind.config.js 예시
module.exports = {
  theme: {
    extend: {
      // @youjeong/moment-token에서 export한 토큰을 가져와 매핑
    },
  },
};
```

또는 패키지에서 제공하는 `@youjeong/moment-token/tailwind` 파일을 임포트하여 사용하세요.

### 4) 원본 JSON 토큰 사용

문서화 도구나 디자인 토큰을 기반으로 하는 자동화 파이프라인에서 사용하려면 원본 JSON 파일을 참조하세요.

```js
import tokens from '@youjeong/moment-token/tokens/tokens.json';
console.log(tokens.colors.primary);
```

---

## 제공되는 엔트리(예시)

패키지는 환경별로 다음 경로/파일을 제공합니다(프로젝트 설정에 따라 경로가 달라질 수 있음):

- `@youjeong/moment-token/css` → 빌드된 CSS(커스텀 프로퍼티)
- `@youjeong/moment-token/scss` → SCSS 변수 파일
- `@youjeong/moment-token/tailwind` → Tailwind용 테마 설정
- `@youjeong/moment-token/tokens/*` → 원본 JSON 토큰들

패키지 내 실제 파일 경로와 네임스페이스는 배포 설정에 따라 달라질 수 있으니, 사용 전 패키지 내용(`node_modules/@youjeong/moment-token`)을 확인하세요.

---

## 커스터마이징 방식

1. CSS 변수 오버라이드
   - 프로젝트 내에서 루트(`:root`)나 특정 스코프에서 CSS 변수를 재정의하여 디자인을 변경할 수 있습니다.

2. SCSS 변수 재정의
   - SCSS 사용 시, 토큰을 불러오기 전에 변수 값을 정의하면 빌드 시 우선 적용됩니다(사용자 프로젝트의 빌드 설정에 따라 다름).

3. Tailwind 커스텀 매핑
   - Tailwind 설정에서 token 값을 참조하여 theme 확장 또는 사용자 유틸리티를 생성하세요.

---

## 개발 및 기여

로컬에서 개발하거나 변경 사항을 빌드하려면:

```bash
git clone <repo-url>
cd moment-token
npm install
npm run build
```

개발 시 유의사항:

- 토큰 구조(JSON)를 변경하면 CSS/SCSS/Tailwind 빌드 파이프라인도 함께 업데이트해야 합니다.
- 변경 사항은 반드시 시각적 회귀가 없는지 검증하세요(스냅샷/스토리북/디자이너 검토 등).

기여 가이드라인:

- Pull Request 전 Lint 및 빌드를 통과시키세요
- 변경 범위가 디자인 토큰에 미치는 영향을 명확히 작성하세요

---

## 배포(간단 가이드)

1. package.json 버전 업데이트
2. npm build 스크립트 실행
3. npm publish --access public (혹은 조직 스코프에 맞게)

배포 전에 README, CHANGELOG, package.json의 main/module/exports 필드가 올바른지 확인하세요.

---

## FAQ

Q. 토큰 색상이나 단위를 프로젝트에서 직접 바꿔도 되나요?
A. 네, CSS 변수나 SCSS 변수로 오버라이드하는 방식을 권장합니다. 다만 디자인 일관성을 위해 핵심 토큰(primary, secondary 등)은 디자인팀과 협의하세요.

Q. Tailwind 버전 호환성은?
A. 현재 Tailwind v4를 기준으로 구성되어 있습니다. 다른 버전에서 사용 시 일부 설정이 달라질 수 있습니다.

---

## 변경 기록(간단)

- v1.0.0 — 초기 릴리스: CSS/SCSS/Tailwind/JSON 토큰 제공

(자세한 변경 사항은 CHANGELOG를 따로 관리하세요.)

---

## 라이선스

MIT

---

문의 및 기여: 리포지토리의 Issues를 사용하거나 유지관리자에게 연락하세요.
