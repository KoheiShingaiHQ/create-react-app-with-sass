# Customizing Create React App : *CSS*

## CSS → Sass
Getting started customizing [create-react-app](https://koheishingaihq.github.io/me/#/article/create-react-app) .

### Install npm module : *node-sass-chokidar*
```bash
# Current path : ~/create-react-app
npm install node-sass-chokidar --save-dev
```

### Install npm module : *npm-run-all*
```bash
# Current path : ~/create-react-app
npm install npm-run-all --save-dev
```

### Edit package.json : *script*
```diff
# Current path : ~/create-react-app/package.json
-    "start": "react-scripts start",
-    "build": "react-scripts build",
+    "start-js": "react-scripts start",
+    "start": "npm-run-all -p watch-css start-js",
+    "build": "npm run build-css && react-scripts build",
+    "build-css": "node-sass-chokidar src/ -o src/",
+    "watch-css": "npm run build-css && node-sass-chokidar src/ -o src/ --watch --recursive",
```

### Add custom sass file to the project
```sass
/* File path : ~/create-react-app/src/Custom.sass */
body
  background: powderblue
```

```diff
# File path : ~/create-react-app/src/App.js
import './App.css';
+ import './Custom.css'
```

→ Running `npm start` compiles `.sass` files to `.css` under `/src` directory.  
→ Open http://localhost:3000 to see `create-react-app` .

> Demo : [koheishingaiHQ.github.io/create-react-app-with-sass](https://koheishingaihq.github.io/create-react-app-with-sass)

![create-react-app-with-sass-screen-shot](https://c1.staticflickr.com/5/4465/36878306283_8811ec8516_b.jpg)
