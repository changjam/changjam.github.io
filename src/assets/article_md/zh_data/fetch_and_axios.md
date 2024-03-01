## 比較 Fetch 與 Axios

在 JavaScript 中，進行網絡請求是一個常見的任務，而 Fetch 和 Axios 是兩個常見的工具，用於執行此類請求。這裡將比較這兩者之間的差異和優缺點。

### Fetch

Fetch 是一個現代的瀏覽器 API，用於進行網絡請求。它提供了一個基於 promise 的接口，可以輕鬆地發送各種類型的請求。

#### 優點：
- 內置於現代瀏覽器，不需要額外安裝任何庫。
- 使用了 Promise API，支持非同步編程，可以更好地處理複雜的請求。
- 輕量級，不需要額外的依賴。

#### 缺點：
- 有些功能需要手動實現，如請求取消、超時管理等。
- 不支持舊版本的瀏覽器，需要使用 polyfill 進行兼容處理。

### Axios

Axios 是一個基於 Promise 的 HTTP 客戶端，可用於瀏覽器和 Node.js 環境。它提供了一個簡潔的 API，使得發送 HTTP 請求變得非常容易。

#### 優點：
- 提供了許多高級功能，如請求取消、CSRF 防護、攔截器等，使得開發更加方便。
- 具有良好的瀏覽器兼容性，支持主流的瀏覽器和 Node.js 環境。
- 支持 Promise 和 async/await 模式，使得非同步編程更加簡單。

#### 缺點：
- 需要額外安裝和引入庫，增加了代碼的體積。
- 在一些瀏覽器環境下可能存在性能問題，特別是在移動設備上。

### 如何選擇

當你需要一個輕量級的解決方案，並且僅在現代瀏覽器中運行時，Fetch 是一個很好的選擇。但如果你需要更多的功能和更好的兼容性，那麼 Axios 是一個更好的選擇。

以下是 Fetch 和 Axios 的示例程式：
### Fetch 範例程式：

```javascript
// 發送 GET 請求
fetch('https://api.example.com/data')
  .then(response => {
    if (!response.ok) {
      throw new Error('網絡錯誤');
    }
    return response.json();
  })
  .then(data => {
    console.log('收到數據：', data);
  })
  .catch(error => {
    console.error('發生錯誤：', error);
  });

// 發送 POST 請求
fetch('https://api.example.com/data', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({ username: 'example', password: '123456' })
})
.then(response => {
  if (!response.ok) {
    throw new Error('網絡錯誤');
  }
  return response.json();
})
.then(data => {
  console.log('收到數據：', data);
})
.catch(error => {
  console.error('發生錯誤：', error);
});
```

### Axios 範例程式：

```javascript
// 引入 Axios
const axios = require('axios');

// 發送 GET 請求
axios.get('https://api.example.com/data')
  .then(response => {
    console.log('收到數據：', response.data);
  })
  .catch(error => {
    console.error('發生錯誤：', error);
  });

// 發送 POST 請求
axios.post('https://api.example.com/data', { username: 'example', password: '123456' })
  .then(response => {
    console.log('收到數據：', response.data);
  })
  .catch(error => {
    console.error('發生錯誤：', error);
  });
```