## Scramble 4 Kids

Juego de palabras desordenadas para practicar vocabulario. La app toma una lista de palabras, mezcla sus letras y el usuario debe adivinar la palabra correcta. Incluye puntaje, limite de errores, limite de saltos y animacion de confetti al acertar.

Repositorio: https://github.com/DsiKorp/scramble-4-kids.git

## Stack y herramientas

- React 19 + TypeScript + Vite.
- Tailwind CSS con shadcn/ui para componentes.
- canvas-confetti para celebraciones.
- lucide-react para iconos.

## Como correr el proyecto

1. Instalar dependencias:
	- `npm install`
2. Levantar entorno dev:
	- `npm run dev`
3. Build de produccion:
	- `npm run build`
4. Lint:
	- `npm run lint`
5. Preview del build:
	- `npm run preview`

## Descripcion del codigo

**Entrada principal**
- [src/main.tsx](src/main.tsx) crea el root de React, carga estilos globales y renderiza `ScrambleWords`.

**Estilos globales**
- [src/index.css](src/index.css) importa Tailwind y define variables de tema, mas utilidades de layout como `bg-gradient`.

**UI principal (useReducer)**
- [src/Scramble/ScrambleWords.tsx](src/Scramble/ScrambleWords.tsx) es el componente principal.
- Usa `useReducer` para manejar el estado del juego y efectos para disparar confetti cuando sube el puntaje.
- Muestra la palabra mezclada, input de adivinanza, puntaje, errores y botones de saltar/reiniciar.
- Cuando no quedan palabras, muestra pantalla de fin con resumen.

**Estado del juego (reducer)**
- [src/Scramble/useReducer/scrambleWordReducer.ts](src/Scramble/useReducer/scrambleWordReducer.ts) define:
  - `ScrambleWordsState` con los contadores, palabra actual, palabra mezclada y lista.
  - `scrambleWordsReducer` con acciones:
	 - `SET_GUESS`: normaliza la adivinanza a mayusculas.
	 - `CHECK_ANSWER`: suma puntos o incrementa errores.
	 - `SKIP_WORD`: salta palabra con limite de saltos.
	 - `START_NEW_GAME`: resetea el estado.
  - `getInitialState()` genera un juego nuevo con palabras mezcladas.

**Version alternativa (useState)**
- [src/Scramble/ScrambleWordsUseState.tsx](src/Scramble/ScrambleWordsUseState.tsx) conserva la misma logica pero con `useState`. No esta montado en [src/main.tsx](src/main.tsx), queda como referencia didactica.

**Utilidades**
- [src/lib/utils.ts](src/lib/utils.ts) provee `cn()` para combinar clases Tailwind.

## Descripcion de package.json

**Scripts**
- `dev`: inicia Vite en modo desarrollo.
- `build`: compila TypeScript y genera el build de Vite.
- `lint`: ejecuta ESLint.
- `preview`: previsualiza el build.

**Dependencias principales**
- `react`, `react-dom`: base de UI.
- `tailwindcss`, `@tailwindcss/vite`: estilos y plugin para Vite.
- `@radix-ui/react-*` y `class-variance-authority`, `clsx`, `tailwind-merge`: base de shadcn/ui.
- `canvas-confetti`: animacion al acertar.
- `lucide-react`: iconos.

**DevDependencies**
- `typescript`, `@types/*`: tipado.
- `eslint`, `typescript-eslint`, `eslint-plugin-react-*`: linting.
- `@vitejs/plugin-react-swc`, `vite`: tooling.
- `tw-animate-css`: animaciones.

## Notas

- El componente principal asume la instalacion de shadcn/ui y Tailwind en Vite.
- Las palabras se definen en el reducer y se mezclan al iniciar cada partida.

## Despliegue

**Netlify**
- Build command: `npm run build`
- Publish directory: `dist`

**Vercel**
- Framework preset: Vite
- Build command: `npm run build`
- Output directory: `dist`
