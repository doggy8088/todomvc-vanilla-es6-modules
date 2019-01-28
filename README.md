# TodoMVC using Vanilla ES6 (Babel to TypeScript)

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

   > 如果你用 VSCode 的話，可以用全部取代的方式，搭配正規表示式就可以一次取代完成：
   >
   > - 搜尋：`import (.*).js';`
   > - 取代：`import $1';`

3. 修正 TypeScript 型別問題

   請參考[此版本](https://github.com/doggy8088/todomvc-vanilla-es6-modules/commit/72286a378b559532699819c314d7b19c3f662091?diff=split)的變更紀錄。

4. 修正 `index.html` 將 `src/app.js` 修改為 `src/app.ts`

   ```html
   <script src="src/app.js"></script>
   ```

   改為

   ```html
   <script src="src/app.ts"></script>
   ```

5. 執行 Parcel 並啟動開發伺服器

   ```sh
   parcel index.html
   ```
