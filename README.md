# Introduction: Setting Up a Standard ReactJS Project Structure with Vite, Yarn, and TypeScript + SWC

This repository contains the source code and a detailed guide on setting up a ReactJS project with Vite, Yarn, and TypeScript + SWC for optimal performance and maintainability.

For the full guide and additional resources, please visit our article:
- [Setting Up a Standard ReactJS Project Structure with Vite, Yarn, and TypeScript + SWC](https://kaizutech.com/reactjs-tutorial/reactjs-part-1-create-a-reactjs-project-with-vite-yarn-and-typescript-swc-for-optimal-performance-434327/).
- [[React.js] - パート1: Vite、Yarn、TypeScript + SWCを使用して最適なパフォーマンスのReactJSプロジェクトを作成](https://kaizutech.com/ja/reactjs-tutorial/reactjs-part-1-create-a-reactjs-project-with-vite-yarn-and-typescript-swc-for-optimal-performance-ja-401225/).

---

# React + TypeScript + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type aware lint rules:

- Configure the top-level `parserOptions` property like this:

```js
export default tseslint.config({
  languageOptions: {
    // other options...
    parserOptions: {
      project: ['./tsconfig.node.json', './tsconfig.app.json'],
      tsconfigRootDir: import.meta.dirname,
    },
  },
})
```

- Replace `tseslint.configs.recommended` to `tseslint.configs.recommendedTypeChecked` or `tseslint.configs.strictTypeChecked`
- Optionally add `...tseslint.configs.stylisticTypeChecked`
- Install [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react) and update the config:

```js
// eslint.config.js
import react from 'eslint-plugin-react'

export default tseslint.config({
  // Set the react version
  settings: { react: { version: '18.3' } },
  plugins: {
    // Add the react plugin
    react,
  },
  rules: {
    // other rules...
    // Enable its recommended rules
    ...react.configs.recommended.rules,
    ...react.configs['jsx-runtime'].rules,
  },
})
```
