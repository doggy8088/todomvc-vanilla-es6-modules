# TodoMVC using Vanilla ES6

## Tutorials

1. 安裝 [parcel-bundler](https://www.npmjs.com/package/parcel-bundler) 套件

   ```sh
   npm install -g parcel-bundler
   ```

   ```sh
   yarn global add parcel-bundler
   ```

2. 修正 `index.html` 將 `type="module"` 移除

   ```html
   <script src="src/app.js"></script>
   ```

3. 加入 npm 設定檔：`package.json`

   你可以透過 `npm init -y` 快速建立預設 `package.json` 檔案。

   ```json
   {
     "name": "todomvc-vanilla-es6-modules",
     "version": "1.0.0",
     "dependencies": {},
     "devDependencies": {},
     "scripts": {}
   }
   ```

4. 安裝 `js-polyfills` 套件

   ```sh
   npm install -D js-polyfills
   ```

5. 修正 `src/app.js` 檔案，匯入 `js-polyfills` 套件

   ```js
   import 'js-polyfills';
   ```

6. 加入 `.gitignore` 版控忽略檔

   ```sh
   # Dependency directories
   node_modules/

   # Yarn Integrity file
   .yarn-integrity

   # parcel-bundler cache (https://parceljs.org/)
   .cache

   # distribution files
   dist/

   # package-lock.json file
   package-lock.json
   ```

7. 執行 Parcel 並啟動開發伺服器

   ```sh
   parcel index.html
   ```
