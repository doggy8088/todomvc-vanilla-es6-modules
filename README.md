# TodoMVC using Vanilla ES6 (TypeScript)

## 設定步驟說明

1. 將所有 `*.js` 檔案批次更名為 `*.ts` 檔案

   ```bat
   cd src
   rename *.js *.ts
   ```

2. 將所有 `*.js` 檔案中 `import` 語法的 `.js` 部分移除

   例如以下 `import` 語法：

   ```sh
   import Controller from './controller.js';
   import {$on} from './helpers.js';
   import Template from './template.js';
   import Store from './store.js';
   import View from './view.js';
   ```

   請全部改成如下：

   ```sh
   import Controller from './controller';
   import {$on} from './helpers';
   import Template from './template';
   import Store from './store';
   import View from './view';
   ```

3. 修正 TypeScript 型別問題

   - 修改 `src/helpers.ts` 檔案

     ```ts
     export function $on(target, type, callback, capture) {
     ```

     將 `callback` 參數改成 optional (可選的)

     ```ts
     export function $on(target, type, callback, capture?) {
     ```

   - 調整 `src/store.ts` 檔案中類別的寫法

     ```ts
     /**
      * @type {ItemList}
     */
     private liveTodos;
     /**
      * Read the local ItemList from localStorage.
     *
     * @returns {ItemList} Current array of todos
     */
     getLocalStorage() {
         return this.liveTodos || JSON.parse(localStorage.getItem(name) || '[]');
     }

     /**
      * Write the local ItemList to localStorage.
     *
     * @param {ItemList} todos Array of todos to write
     */
     setLocalStorage(todos) {
         localStorage.setItem(name, JSON.stringify(this.liveTodos = todos));
     }

     /**
      * @param {!string} name Database name
     * @param {function()} [callback] Called when the Store is ready
     */
     constructor(name, callback?) {
         if (callback) {
             callback();
         }
     }
     ```

4. 加入 npm 設定檔：`package.json`

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

5. 加入 [js-polyfills](https://www.npmjs.com/package/js-polyfills) 套件，並加入 `src/app.ts`

   ```ts
   import 'js-polyfills';
   ```

6. 執行 Parcel 並啟動開發伺服器

   ```sh
   parcel index.html
   ```
