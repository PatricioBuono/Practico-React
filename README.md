# React + TypeScript + Vite

Esta plantilla proporciona una configuración mínima para hacer funcionar React con Vite, habilitando la recarga rápida (HMR) y algunas reglas de ESLint.

Actualmente, hay dos plugins oficiales disponibles:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) usa [Babel](https://babeljs.io/) para la recarga rápida.
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) usa [SWC](https://swc.rs/) para la recarga rápida.

## Expandiendo la configuración de ESLint

Si estás desarrollando una aplicación para producción, te recomendamos actualizar la configuración para habilitar reglas de linting que consideren el tipo de datos:

- Configura la propiedad `parserOptions` a nivel superior de esta manera:

```js
export default tseslint.config({
  languageOptions: {
    // otras opciones...
    parserOptions: {
      project: ['./tsconfig.node.json', './tsconfig.app.json'],
      tsconfigRootDir: import.meta.dirname,
    },
  },
})
- Cambia tseslint.configs.recommended por tseslint.configs.recommendedTypeChecked o tseslint.configs.strictTypeChecked.
- Opcionalmente, agrega ...tseslint.configs.stylisticTypeChecked.
- Instala eslint-plugin-react y actualiza la configuración:
// eslint.config.js
import react from 'eslint-plugin-react'

export default tseslint.config({
  // Establece la versión de React
  settings: { react: { version: '18.3' } },
  plugins: {
    // Agrega el plugin de React
    react,
  },
  rules: {
    // otras reglas...
    // Habilita las reglas recomendadas de React
    ...react.configs.recommended.rules,
    ...react.configs['jsx-runtime'].rules,
  },
})
