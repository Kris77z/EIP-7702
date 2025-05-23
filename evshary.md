---
timezone: UTC+8
---

# evshary

1. 自我介绍：
     Web3 新手，最近對區塊鏈相關知識非常有興趣，想透過殘酷共學跟大家一起學習。
2. 你认为你会完成本次残酷学习吗？
     會
3. 你的联系方式（推荐 Telegram）
     t.me/evshary

## Notes

<!-- Content_START -->

### 2025.05.14

#### 為何需要 EIP-7702 （目前遇到什麼問題）

以太坊主要有兩種位址：
1. EOA (Externally Owned Accounts)
2. 智能合約帳戶 (Contract Account)

在 EIP-7702 之前，EOA 的功能相對簡單，主要是發送交易功能。不能像是智能合約錢包能夠執行程式碼。
因此使用者必須要先把資產轉移到智能合約錢包，對使用者來說十分麻煩。

在 EIP-7702 之後，EOA 就能支援批次交易處理、gas 贊助、或是複雜權限管理，少了一個轉帳的動作。EOA 更加接近抽象帳戶的概念。

#### EIP-7702 的運作方式

1. 使用者用 EOA 創建新的交易類型
2. 交易中會指定一個智能合約地址，EOA 在該交易中會臨時地像這個智能合約一樣運作
3. 用 EOA 私鑰簽署交易
4. EVM 在處理這筆交易時，會臨時地將發送方的 EOA 視為位於指定智能合約地址的合約，並執行該合約地址上的程式碼
5. 完成交易後，EOA 會回復正常模式

#### 引入 EIP-7702 的可能風險

1. 委託的智能合約如果沒有適當的存取限制，攻擊者可以存取 EOA 內的所有資產
2. 開發者確保初始化程式碼有正確的執行，不然可能會有邏輯錯誤或是被攻擊者利用
3. 委託程式碼不會清除現有儲存，因此某些變數在切換合約時可能會遺留舊數據
4. 過去 EOA 相對來說被認為比較安全，現在也引入了智能合約相關的風險

### 2025.05.15

<!-- Content_END -->
