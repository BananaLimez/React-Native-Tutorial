# 02 - NativeWind Installation Guide

This guide will walk you through the setup process of **NativeWind** in your React Native project.

---

## 1. Install NativeWind Package

```bash
npm install nativewind react-native-reanimated@~3.17.4 react-native-safe-area-context@5.4.0
npm install --dev tailwindcss@^3.4.17 prettier-plugin-tailwindcss@^0.5.11
```

---

## 2. Create Tailwind Config

```bash
npx tailwindcss init
```

Generated `tailwind.config.js` should look like this:

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  // NOTE: Update this to include the paths to all files that contain NativeWind classes.
  content: [
    "./App.tsx",
    "./components/**/*.{js,jsx,ts,tsx}",
    "./app/**/*.{js,jsx,ts,tsx}"
  ],
  presets: [require("nativewind/preset")],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

---

## 3. Create Global CSS

In the **root directory**, create a file named `global.css` and add the following:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

---

## 4. Add Babel Preset

Update your `babel.config.js`:

```js
module.exports = function (api) {
  api.cache(true);
  return {
    presets: [
      ["babel-preset-expo", { jsxImportSource: "nativewind" }],
      "nativewind/babel",
    ],
  };
};
```

---

## 5. Add Metro Config

Create or update your `metro.config.js`:

```js
const { getDefaultConfig } = require("expo/metro-config");
const { withNativeWind } = require('nativewind/metro');
 
const config = getDefaultConfig(__dirname)
 
module.exports = withNativeWind(config, { input: './global.css' })
```

---

## 6. Import CSS File

Usually imported inside `_layout.tsx`:

```tsx
import '@/global.css'
```

*(because it’s in the root folder)*

---

## 7. Modify `app.json`

```json
{
  "expo": {
    "web": {
      "bundler": "metro"
    }
  }
}
```

---

## 8. TypeScript Setup

Create a `nativewind-env.d.ts` file with:

```ts
/// <reference types="nativewind/types" />
```

---

✅ NativeWind installation for React Native is now complete!
