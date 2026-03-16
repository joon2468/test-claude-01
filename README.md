# React + TypeScript + Vite

## 배포 정보

### GitHub Pages
- **URL**: https://joon2468.github.io/test-claude-01/
- **저장소**: public repo 필수 (private은 유료 플랜 필요)
- **설정**: `vite.config.ts`에 `base: '/test-claude-01/'` 추가 필요 (repo명과 일치)

#### 배포 방식 비교

| | 수동 배포 | GitHub Actions 자동 배포 |
|---|---|---|
| **방법** | `npm run deploy` 직접 실행 | main 브랜치에 push하면 자동 실행 |
| **속도** | 로컬 빌드 속도 | 2~5분 (가상 서버 실행) |
| **Actions 사용량** | 해당 없음 | push마다 소모 |

#### GitHub Actions 설정
- 워크플로우 파일: `.github/workflows/deploy.yml`
- main 브랜치 push 시 자동으로 빌드 + `gh-pages` 브랜치로 배포
- **권한 설정 필요**: Settings → Actions → General → Workflow permissions → "Read and write permissions"

#### Actions 무료 제한
- **public repo**: 무제한 무료
- **private repo**: 월 2,000분 제한
- push를 자주 하면 Actions가 그만큼 실행되므로 커밋은 자주, push는 적당히

---



This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Oxc](https://oxc.rs)
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/)

## React Compiler

The React Compiler is not enabled on this template because of its impact on dev & build performances. To add it, see [this documentation](https://react.dev/learn/react-compiler/installation).

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type-aware lint rules:

```js
export default defineConfig([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...

      // Remove tseslint.configs.recommended and replace with this
      tseslint.configs.recommendedTypeChecked,
      // Alternatively, use this for stricter rules
      tseslint.configs.strictTypeChecked,
      // Optionally, add this for stylistic rules
      tseslint.configs.stylisticTypeChecked,

      // Other configs...
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
])
```

You can also install [eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x) and [eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom) for React-specific lint rules:

```js
// eslint.config.js
import reactX from 'eslint-plugin-react-x'
import reactDom from 'eslint-plugin-react-dom'

export default defineConfig([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...
      // Enable lint rules for React
      reactX.configs['recommended-typescript'],
      // Enable lint rules for React DOM
      reactDom.configs.recommended,
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
])
```
