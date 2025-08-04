# Prelude
Those folowing instructions are mainly meant to be run on a Windows powered device. Those are the 08-2025 working instructions, and can become outdated with the time. 

# MAIN INIT INSTRUCTIONS 
First, to create the project with Vite, especially a React TS project, run in your terminal (cmd) : 
```bash
npm create vite@latest project-name -- --template react-ts
```

Then go to the project : 
```bash
cd project-name
```

Then install Tailwind : 
```bash
npm install -D tailwindcss@latest postcss@latest autoprefixer@latest
```

Once Tailwind is installed, initialize it in your project : 
```bash
npx tailwindcss-cli@latest init -p
```
Note that this command is not optimized, and is meant to dodge an issue in which tailwind is not well rekognized by npx, so it install the tailwind CLI temporary, the "good" instruction is the following : `npx tailwindcss init -p`.

# FINAL CONFIG
Anyway, once tailwind is correctly set up in your project, some configuration adjustments are required.

You can launch your project with `code .` if vs code is added to your `PATH`. Once you've opened your project follow the following instructions. 

### tailwind config
First, go to the `tailwind.config.js` file, and make sure that the **content** section look to this : 
```js
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
};
```
This will ensure all your .js/.ts/.jsx/.tsx files in ./src to be able to use tailwind (and also index.html). Of course you can add what you want in `tailwind.config.js`but make sure that **content** contains at least those 2 lines. 

### postcss config 
Search a file named `postcss.config.cjs` and make sure that it's extension is `.cjs` and not `.js`. If you're in the wrong case, rename the file by changing it's extension. 

Then make sure the file is like this : 
```js
module.exports = {
  plugins: [
    require('@tailwindcss/postcss')(),
    require('autoprefixer'),
  ],
};
```

### final postcss verification
Sometimes, postcss is not well installed, enter this command in your terminal (at the root of your project) : 
```bash
 npm install -D @tailwindcss/postcss
```

### index css
Next, go to the `./src/index.css` file -if it does not exist create it, and add those lines in the top of it : 
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```
Don't mind if they're underlined. 

### main
Finally, make sure that your main project file `./src/main.tsx` contains this : 
```tsx
import './index.css'
```

---

You can now advance in your project ! To run it, type in your terminal at the root of your project : 
```bash
npm run dev 
```
