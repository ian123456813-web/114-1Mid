# 第2次隨堂題目-隨堂-QZ2
>
>學號：112111138   (學號和姓名都要寫)
><br />
>姓名：郭銘諺
>

本份文件包含以下主題：(至少需下面兩項，若是有多者可以自行新增)
- [x] 說明內容

## 說明程式與內容
請在撰寫"說明程式與內容"該塊內容，請把原該塊內上述敘述刪除，該塊上述內容只是用來指引該怎麼撰寫內容。

1. a.

Ans: 物件 類別




1. b.

Ans:// ==========================================
// 商品庫存與查詢系統
// ==========================================
// 功能說明：
//  getLowStock - 篩選出庫存不足的商品
//  updateStock - 批次更新商品庫存
// ==========================================

// ==========================================
//  取得低庫存商品清單
// ==========================================

/**
 * 篩選出庫存量少於 10 的商品名稱
 *
 * @param {Array} products - 商品陣列，每個元素包含 { name, stock }
 * @returns {Array} 庫存不足商品的名稱陣列
 *
 * 範例：
 *   輸入: [{ name: "mouse", stock: 5 }, { name: "keyboard", stock: 25 }]
 *   輸出: ["mouse"]
 */
function getLowStock(products) {
 
}


// ==========================================
//  批次更新商品庫存
// ==========================================

/**
 * 根據更新物件批次更新商品庫存
 * 注意：不修改原始陣列，回傳新的陣列
 *
 * @param {Array} products - 原始商品陣列
 * @param {Object} updates - 要更新的商品庫存，格式：{ 商品名: 新庫存量 }
 * @returns {Array} 更新後的新商品陣列
 *
 * 範例：
 *   products = [{ name: "mouse", stock: 5 }]
 *   updates = { mouse: 15 }
 *   結果: [{ name: "mouse", stock: 15 }]
 */
function updateStock(products, updates) {
  
}


// ==========================================
// 測試範例
// ==========================================

// 測試資料
const products = [
  { name: "keyboard", stock: 25 },
  { name: "mouse", stock: 5 },
  { name: "monitor", stock: 8 },
  { name: "usb cable", stock: 40 }
];

console.log("==========================================");
console.log("原始商品資料：");
console.log("==========================================");
console.log(products);
console.log("");

// ------------------------------------------
// 測試 (a) getLowStock
// ------------------------------------------
console.log("==========================================");
console.log("(a) 測試 getLowStock - 查詢低庫存商品");
console.log("==========================================");

const lowStockItems = getLowStock(products);
console.log("庫存少於 10 的商品：", lowStockItems);
console.log("預期結果：['mouse', 'monitor']");

// 檢查結果是否正確
let isCorrect = true;
if (lowStockItems.length !== 2) {
  isCorrect = false;
}
if (lowStockItems[0] !== "mouse" || lowStockItems[1] !== "monitor") {
  isCorrect = false;
}
console.log("測試結果：", isCorrect ? "✅ 通過" : "❌ 失敗");
console.log("");

// ------------------------------------------
// 測試 (b) updateStock
// ------------------------------------------
console.log("==========================================");
console.log("(b) 測試 updateStock - 批次更新庫存");
console.log("==========================================");

const updates = {
  mouse: 15,
  monitor: 20
};

console.log("要更新的商品：", updates);
console.log("");

const updatedProducts = updateStock(products, updates);

console.log("更新後的商品資料：");
console.log(updatedProducts);
console.log("");

console.log("原始商品資料是否被修改？");
console.log(products);
console.log("原始資料保持不變：",
  products[1].stock === 5 && products[2].stock === 8 ? "✅ 通過（未被修改）" : "❌ 失敗（被修改了）"
);
console.log("");

console.log("新陣列的庫存是否正確更新？");
console.log("mouse 的庫存：", updatedProducts[1].stock, " (預期: 15)", updatedProducts[1].stock === 15 ? "✅" : "❌");
console.log("monitor 的庫存：", updatedProducts[2].stock, " (預期: 20)", updatedProducts[2].stock === 20 ? "✅" : "❌");
console.log("keyboard 的庫存：", updatedProducts[0].stock, " (預期: 25，未變)", updatedProducts[0].stock === 25 ? "✅" : "❌");
console.log("");


// ==========================================
// 進階測試：組合使用兩個函式
// ==========================================
console.log("==========================================");
console.log("進階測試：組合使用兩個函式");
console.log("==========================================");

// 步驟 1: 找出低庫存商品
const lowStock = getLowStock(products);
console.log("步驟 1 - 低庫存商品：", lowStock);

// 步驟 2: 為低庫存商品補貨（設定庫存為 50）
const restockUpdates = {};
lowStock.forEach(name => {
  restockUpdates[name] = 50;
});
console.log("步驟 2 - 補貨清單：", restockUpdates);

// 步驟 3: 執行補貨
const restockedProducts = updateStock(products, restockUpdates);
console.log("步驟 3 - 補貨後的商品：", restockedProducts);

// 步驟 4: 檢查是否還有低庫存商品
const stillLowStock = getLowStock(restockedProducts);
console.log("步驟 4 - 補貨後的低庫存商品：", stillLowStock);
console.log("所有商品庫存充足：", stillLowStock.length === 0 ? "✅ 是" : "❌ 否");
console.log("");


// ==========================================
// 匯出函式（供其他檔案使用）
// ==========================================

// 如果在 Node.js 環境中使用，可以匯出這些函式
// 在其他檔案中可以使用：const { getLowStock, updateStock } = require('./sol2.js');
if (typeof module !== 'undefined' && module.exports) {
  module.exports = {
    getLowStock,
    updateStock
  };
}


// ==========================================
// 補充說明：關鍵概念解析
// ==========================================

/*

1. filter() 方法
   - 用途：篩選陣列中符合條件的元素
   - 語法：array.filter(callback)
   - 回傳：新陣列（只包含符合條件的元素）
   - 範例：[1, 2, 3, 4].filter(num => num > 2)  // [3, 4]

2. map() 方法
   - 用途：轉換陣列中的每個元素
   - 語法：array.map(callback)
   - 回傳：新陣列（每個元素都經過轉換）
   - 範例：[1, 2, 3].map(num => num * 2)  // [2, 4, 6]

3. 展開運算子 (...)
   - 用途：複製物件或陣列（淺拷貝）
   - 語法：{ ...原物件 } 或 [ ...原陣列 ]
   - 重要：可以在複製的同時覆寫特定屬性
   - 範例：
     const obj1 = { a: 1, b: 2 };
     const obj2 = { ...obj1, b: 3 };  // { a: 1, b: 3 }

4. 不可變性 (Immutability)
   - 原則：不修改原始資料，而是創建新的資料
   - 優點：
     * 避免副作用（side effects）
     * 容易追蹤資料變化
     * 方便實作復原功能
     * 在 React 等框架中是最佳實踐
   - 本題要求「原有 products 不得被改變」就是在強調不可變性

5. Method Chaining（方法鏈）
   - 將多個方法串接在一起
   - 範例：
     products
       .filter(p => p.stock < 10)
       .map(p => p.name)
   - 優點：程式碼簡潔、易讀

*/
<!-- 請撰寫時，最後一句話再寫一次 --> - 優點：程式碼簡潔、易讀


1. c.

Ans:
// ==========================================
// 商品庫存與查詢系統
// ==========================================
// 功能說明：
//  getLowStock - 篩選出庫存不足的商品
//  updateStock - 批次更新商品庫存
// ==========================================

// ==========================================
//  取得低庫存商品清單
// ==========================================

/**
 * 篩選出庫存量少於 10 的商品名稱
 *
 * @param {Array} products - 商品陣列，每個元素包含 { name, stock }
 * @returns {Array} 庫存不足商品的名稱陣列
 *
 * 範例：
 *   輸入: [{ name: "mouse", stock: 5 }, { name: "keyboard", stock: 25 }]
 *   輸出: ["mouse"]
 */
function getLowStock(products) {
 
}


// ==========================================
//  批次更新商品庫存
// ==========================================

/**
 * 根據更新物件批次更新商品庫存
 * 注意：不修改原始陣列，回傳新的陣列
 *
 * @param {Array} products - 原始商品陣列
 * @param {Object} updates - 要更新的商品庫存，格式：{ 商品名: 新庫存量 }
 * @returns {Array} 更新後的新商品陣列
 *
 * 範例：
 *   products = [{ name: "mouse", stock: 5 }]
 *   updates = { mouse: 15 }
 *   結果: [{ name: "mouse", stock: 15 }]
 */
function updateStock(products, updates) {
  
}


// ==========================================
// 測試範例
// ==========================================

// 測試資料
const products = [
  { name: "keyboard", stock: 25 },
  { name: "mouse", stock: 5 },
  { name: "monitor", stock: 8 },
  { name: "usb cable", stock: 40 }
];

console.log("==========================================");
console.log("原始商品資料：");
console.log("==========================================");
console.log(products);
console.log("");

// ------------------------------------------
// 測試 (a) getLowStock
// ------------------------------------------
console.log("==========================================");
console.log("(a) 測試 getLowStock - 查詢低庫存商品");
console.log("==========================================");

const lowStockItems = getLowStock(products);
console.log("庫存少於 10 的商品：", lowStockItems);
console.log("預期結果：['mouse', 'monitor']");

// 檢查結果是否正確
let isCorrect = true;
if (lowStockItems.length !== 2) {
  isCorrect = false;
}
if (lowStockItems[0] !== "mouse" || lowStockItems[1] !== "monitor") {
  isCorrect = false;
}
console.log("測試結果：", isCorrect ? "✅ 通過" : "❌ 失敗");
console.log("");

// ------------------------------------------
// 測試 (b) updateStock
// ------------------------------------------
console.log("==========================================");
console.log("(b) 測試 updateStock - 批次更新庫存");
console.log("==========================================");

const updates = {
  mouse: 15,
  monitor: 20
};

console.log("要更新的商品：", updates);
console.log("");

const updatedProducts = updateStock(products, updates);

console.log("更新後的商品資料：");
console.log(updatedProducts);
console.log("");

console.log("原始商品資料是否被修改？");
console.log(products);
console.log("原始資料保持不變：",
  products[1].stock === 5 && products[2].stock === 8 ? "✅ 通過（未被修改）" : "❌ 失敗（被修改了）"
);
console.log("");

console.log("新陣列的庫存是否正確更新？");
console.log("mouse 的庫存：", updatedProducts[1].stock, " (預期: 15)", updatedProducts[1].stock === 15 ? "✅" : "❌");
console.log("monitor 的庫存：", updatedProducts[2].stock, " (預期: 20)", updatedProducts[2].stock === 20 ? "✅" : "❌");
console.log("keyboard 的庫存：", updatedProducts[0].stock, " (預期: 25，未變)", updatedProducts[0].stock === 25 ? "✅" : "❌");
console.log("");


// ==========================================
// 進階測試：組合使用兩個函式
// ==========================================
console.log("==========================================");
console.log("進階測試：組合使用兩個函式");
console.log("==========================================");

// 步驟 1: 找出低庫存商品
const lowStock = getLowStock(products);
console.log("步驟 1 - 低庫存商品：", lowStock);

// 步驟 2: 為低庫存商品補貨（設定庫存為 50）
const restockUpdates = {};
lowStock.forEach(name => {
  restockUpdates[name] = 50;
});
console.log("步驟 2 - 補貨清單：", restockUpdates);

// 步驟 3: 執行補貨
const restockedProducts = updateStock(products, restockUpdates);
console.log("步驟 3 - 補貨後的商品：", restockedProducts);

// 步驟 4: 檢查是否還有低庫存商品
const stillLowStock = getLowStock(restockedProducts);
console.log("步驟 4 - 補貨後的低庫存商品：", stillLowStock);
console.log("所有商品庫存充足：", stillLowStock.length === 0 ? "✅ 是" : "❌ 否");
console.log("");


// ==========================================
// 匯出函式（供其他檔案使用）
// ==========================================

// 如果在 Node.js 環境中使用，可以匯出這些函式
// 在其他檔案中可以使用：const { getLowStock, updateStock } = require('./sol2.js');
if (typeof module !== 'undefined' && module.exports) {
  module.exports = {
    getLowStock,
    updateStock
  };
}


// ==========================================
// 補充說明：關鍵概念解析
// ==========================================

/*

1. filter() 方法
   - 用途：篩選陣列中符合條件的元素
   - 語法：array.filter(callback)
   - 回傳：新陣列（只包含符合條件的元素）
   - 範例：[1, 2, 3, 4].filter(num => num > 2)  // [3, 4]

2. map() 方法
   - 用途：轉換陣列中的每個元素
   - 語法：array.map(callback)
   - 回傳：新陣列（每個元素都經過轉換）
   - 範例：[1, 2, 3].map(num => num * 2)  // [2, 4, 6]

3. 展開運算子 (...)
   - 用途：複製物件或陣列（淺拷貝）
   - 語法：{ ...原物件 } 或 [ ...原陣列 ]
   - 重要：可以在複製的同時覆寫特定屬性
   - 範例：
     const obj1 = { a: 1, b: 2 };
     const obj2 = { ...obj1, b: 3 };  // { a: 1, b: 3 }

4. 不可變性 (Immutability)
   - 原則：不修改原始資料，而是創建新的資料
   - 優點：
     * 避免副作用（side effects）
     * 容易追蹤資料變化
     * 方便實作復原功能
     * 在 React 等框架中是最佳實踐
   - 本題要求「原有 products 不得被改變」就是在強調不可變性

5. Method Chaining（方法鏈）
   - 將多個方法串接在一起
   - 範例：
     products
       .filter(p => p.stock < 10)
       .map(p => p.name)
   - 優點：程式碼簡潔、易讀

*/

<!--  請撰寫時，第一句話再寫一次  --> // ==========================================

2. a.

Ans:
//1、引入http模組
const http = require('http');

//2、創建http伺服器
const server = http.createServer(function (request, response) {
  const url = request.url;  //獲取請求位址
  console.log(url)
  var answer = '';  //設置回應內容

  // 請寫 switch完成各個收到不同的請求以及輸出不同的回應字串 (使用 switch)
  



  
  response.setHeader('Content-Type', 'text/plain;charset=utf-8'); //設置回應頭編碼為utf-8，避免中文亂碼
  response.end(answer);
});
//3、啟動伺服器監聽8888埠
server.listen('8888', function () {
  console.log("伺服器啟動成功，訪問：http://127.0.0.1:8888")
})

<!--  請撰寫時，第一句話再寫一次  --> //1、引入http模組

2. b.

Ans:
//1、引入http模組
const http = require('http');

//2、創建http伺服器
const server = http.createServer(function (request, response) {
  const url = request.url;  //獲取請求位址
  console.log(url)
  var answer = '';  //設置回應內容

  // 請寫 switch完成各個收到不同的請求以及輸出不同的回應字串 (使用 switch)
  



  
  response.setHeader('Content-Type', 'text/plain;charset=utf-8'); //設置回應頭編碼為utf-8，避免中文亂碼
  response.end(answer);
});
//3、啟動伺服器監聽8888埠
server.listen('8888', function () {
  console.log("伺服器啟動成功，訪問：http://127.0.0.1:8888")
})

<!--  請撰寫時，第一句話再寫一次  -->//1、引入http模組

2. c.

Ans:
//1、引入http模組
const http = require('http');

//2、創建http伺服器
const server = http.createServer(function (request, response) {
  const url = request.url;  //獲取請求位址
  console.log(url)
  var answer = '';  //設置回應內容

  // 請寫 switch完成各個收到不同的請求以及輸出不同的回應字串 (使用 switch)
  



  
  response.setHeader('Content-Type', 'text/plain;charset=utf-8'); //設置回應頭編碼為utf-8，避免中文亂碼
  response.end(answer);
});
//3、啟動伺服器監聽8888埠
server.listen('8888', function () {
  console.log("伺服器啟動成功，訪問：http://127.0.0.1:8888")
})

<!--  請撰寫時，第一句話和最後一句再寫一次  -->//1、引入http模組   console.log("伺服器啟動成功，訪問：http://127.0.0.1:8888")

2. d.

Ans:
// ==========================================
// Node.js + EJS 網頁伺服器
// ==========================================
// 功能說明：
// 1. 提供多頁面路由（首頁、計算器、404頁面）
// 2. 支援 EJS 模板動態渲染
// 3. 處理靜態資源（CSS、JS、圖片等）
// 4. 自動錯誤處理與 404 頁面導向
// ==========================================

// ------------------------------------------
// 引入必要的 Node.js 核心模組
// ------------------------------------------

// http 模組：用於創建 HTTP 伺服器
const http = require('http');

// fs 模組 (File System)：用於讀取檔案系統中的文件
const fs = require('fs');

// ejs 模組：用於渲染 EJS 模板引擎，將動態內容嵌入 HTML
const ejs = require('ejs');

// path 模組：用於處理和解析文件路徑，提取副檔名
const path = require('path');

// ==========================================
// 創建並配置 HTTP 伺服器
// ==========================================

http.createServer((req, res) => {
  // req (request): 請求物件，包含客戶端發送的所有資訊（URL、標頭等）
  // res (response): 回應物件，用於向客戶端發送回應（HTML、狀態碼等）

  // ==========================================
  // 步驟 1: URL 路由與頁面分派
  // ==========================================

  // 宣告兩個變數來處理不同類型的請求：
  // filePath: 儲存要渲染的 EJS 模板文件路徑
  // fileOtherFile: 儲存靜態資源（CSS、JS 等）的路徑
  let filePath = '';
  let fileOtherFile = '';

  // Switch根據不同路由要寫的部分





  

  // ==========================================
  // 步驟 2: 判斷文件類型（提取副檔名）
  // ==========================================

  // 使用三元運算子判斷要從哪個路徑提取副檔名：
  // - 如果 fileOtherFile 是空字串 → 從 filePath 提取（代表是 EJS 頁面）
  // - 如果 fileOtherFile 有值 → 從 fileOtherFile 提取（代表是靜態資源）
  //
  // path.extname() 函數會提取文件的副檔名
  // 範例：
  //   path.extname('/index.ejs') → '.ejs'
  //   path.extname('/style.css') → '.css'
  //   path.extname('/script.js') → '.js'
  const extname = (fileOtherFile === '') ? path.extname(filePath) : path.extname(fileOtherFile);

  // ==========================================
  // 步驟 3: 定義 MIME 類型映射表
  // ==========================================

  // MIME 類型（Content-Type）告訴瀏覽器如何處理接收到的文件
  // 如果設定錯誤，可能導致：
  // - CSS 不生效（被當作純文字）
  // - JavaScript 無法執行
  // - 圖片無法顯示
  const contentTypes = {
    '.html': 'text/html; charset=utf-8',        // HTML 網頁文件
    '.ejs': 'text/html; charset=utf-8',         // EJS 模板（渲染後輸出為 HTML）
    '.js': 'text/javascript; charset=utf-8',    // JavaScript 腳本文件
    '.css': 'text/css; charset=utf-8',          // CSS 樣式表文件
    '.json': 'application/json',                // JSON 資料格式
    '.png': 'image/png',                        // PNG 圖片格式
    '.jpg': 'image/jpg',                        // JPG/JPEG 圖片格式
    '.gif': 'image/gif',                        // GIF 動畫圖片
    '.svg': 'image/svg+xml',                    // SVG 向量圖形
    '.ico': 'image/x-icon'                      // 網站 favicon 圖示
  };

  // ==========================================
  // 步驟 4: 查找對應的 Content-Type
  // ==========================================

  // 從映射表中查找當前文件對應的 MIME 類型
  // 使用 || 運算子提供預設值：
  // - 如果在映射表中找到對應的副檔名，使用該 MIME 類型
  // - 如果找不到，預設使用 'text/plain'（純文字格式）
  const contentType = contentTypes[extname] || 'text/plain';

  // ==========================================
  // 請求處理：根據文件類型分流
  // ==========================================

  // 使用 if-else 判斷式區分兩種處理方式：
  // 1. EJS 模板渲染（動態內容）
  // 2. 靜態文件傳送（CSS、JS、圖片等）

  // ------------------------------------------
  // 處理方式 A: EJS 模板渲染
  // ------------------------------------------
  // 適用情況：extname === '.ejs'
  // 處理頁面：index.ejs, index2.ejs, index3.ejs
  if (extname === '.ejs') {

    // 讀取 EJS 模板文件
    // 參數說明：
    //   ('.' + filePath): 構建完整路徑，'.' 代表當前目錄
    //                     例如：'/index.ejs' → './index.ejs'
    //   'utf8': 指定文件編碼格式為 UTF-8，確保中文正確顯示
    //   (err, template): 回調函數的參數
    //                    err: 錯誤物件（若成功則為 null）
    //                    template: 讀取到的文件內容（字串）
    fs.readFile(('.' + filePath), 'utf8', (err, template) => {

      // 錯誤處理：檢查文件是否讀取失敗
      if (err) {
        // 設定 HTTP 狀態碼 500（Internal Server Error - 伺服器內部錯誤）
        // 這表示伺服器嘗試處理請求時發生問題
        res.writeHead(500, { 'Content-Type': 'text/html; charset=utf-8' });

        // 向客戶端發送錯誤訊息，包含具體的錯誤原因
        res.end('錯誤：無法讀取模板文件 - ' + err.message);

        // 使用 return 提前結束函數，避免執行後續的渲染代碼
        return;
      }

      // 使用 EJS 引擎渲染模板
      // ejs.render() 會：
      // 1. 解析 EJS 語法（如 <%= %>, <% %> 等）
      // 2. 執行嵌入的 JavaScript 代碼
      // 3. 將結果轉換成純 HTML 字串
      const html = ejs.render(template);

      // 設定 HTTP 回應標頭
      // 狀態碼 200: OK（請求成功）
      // Content-Type: 告訴瀏覽器這是 HTML 文件，使用 UTF-8 編碼
      res.writeHead(200, { 'Content-Type': 'text/html; charset=utf-8' });

      // 將渲染完成的 HTML 發送給客戶端（瀏覽器）
      res.end(html);
    });

  } else {
    // ------------------------------------------
    // 處理方式 B: 靜態文件傳送
    // ------------------------------------------
    // 適用情況：extname !== '.ejs'（例如 .css, .js, .png 等）
    // 處理文件：style.css, style2.css, style3.css, script.js

    // 構建完整的靜態文件路徑
    // 在路徑前加上 '.' 表示當前工作目錄
    // 範例：
    //   '/style.css' → './style.css'
    //   '/script.js' → './script.js'
    const staticFilePath = '.' + fileOtherFile;

    // 讀取靜態文件
    // 注意：這裡「沒有」指定 'utf8' 編碼
    // 原因：某些文件是二進制格式（如圖片、字型），不能用文字方式讀取
    // fs.readFile 會以 Buffer 格式讀取文件（可處理任何類型的文件）
    fs.readFile(staticFilePath, (err, content) => {

      // 檢查靜態文件是否讀取失敗
      if (err) {
        // ------------------------------------------
        // 靜態文件不存在 → 顯示 404 錯誤頁面
        // ------------------------------------------

        // 當靜態資源載入失敗時（例如：請求不存在的文件或網址）
        // 不直接回傳錯誤訊息，而是顯示友善的 404 錯誤頁面（index3.ejs）

        // 設定 HTTP 狀態碼 404（找不到資源）
        res.writeHead(404, { 'Content-Type': 'text/html; charset=utf-8' });

        // 向客戶端發送 404 錯誤訊息
        res.end('404 - 找不到文件：');

      } else {
        // ------------------------------------------
        // 靜態文件讀取成功 → 直接發送文件內容
        // ------------------------------------------

        // 設定 HTTP 狀態碼 200（成功）
        // Content-Type 根據文件副檔名自動設定（從 contentTypes 映射表查詢）
        // 例如：
        //   .css 檔案 → 'text/css; charset=utf-8'
        //   .js 檔案 → 'text/javascript; charset=utf-8'
        //   .png 檔案 → 'image/png'
        res.writeHead(200, { 'Content-Type': contentType });

        // 將文件內容發送給客戶端
        // content 變數的類型取決於文件：
        // - 文字文件（CSS、JS）：Buffer 會自動轉換為文字
        // - 二進制文件（圖片）：直接以 Buffer 形式傳送
        res.end(content);
      }
    });
  }

// ==========================================
// 啟動伺服器並開始監聽請求
// ==========================================

// .listen() 方法啟動伺服器並監聽指定的端口
// 參數說明：
//   3000: 端口號（Port），伺服器將在此端口接收請求
//   回調函數: 伺服器成功啟動後執行的函數
}).listen(3000, () => {

  // 在終端機（控制台）輸出訊息，告知開發者伺服器已啟動
  // 使用者可以透過瀏覽器訪問 http://localhost:3000 來查看網站
  console.log('伺服器已啟動！請訪問 http://localhost:3000');
  console.log('可用路由：');
  console.log('  - http://localhost:3000');
  console.log('  - http://localhost:3000/calculator');
  console.log('  - 其他路徑將顯示 404 錯誤頁面');
});

// ==========================================
// 程式運行流程總結
// ==========================================
//
// 1. 使用者在瀏覽器輸入網址（例如：http://localhost:3000）
// 2. 瀏覽器發送 HTTP 請求到伺服器
// 3. 伺服器的 createServer 回調函數被觸發
// 4. 根據 req.url 判斷要返回哪個頁面或資源
// 5. 如果是 EJS 頁面：
//    - 讀取 EJS 模板文件
//    - 使用 ejs.render() 渲染成 HTML
//    - 將 HTML 發送給瀏覽器
// 6. 如果是靜態資源（CSS、JS）：
//    - 嘗試讀取對應的文件
//    - 如果存在，直接發送文件內容
//    - 如果不存在，顯示 404 錯誤頁面
// 7. 瀏覽器接收到內容並顯示給使用者
//
// ==========================================


