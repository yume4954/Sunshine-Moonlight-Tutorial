# Sunshine

## Sunshine 是什麼

Sunshine 是一套開源的遊戲串流 / 遠端桌面串流服務端程式，可以配合 Moonlight 等客戶端使用。

官方下載頁面：

https://github.com/LizardByte/Sunshine/releases

Windows 版本請下載：

`sunshine-windows-installer.exe`

---

## 安裝 Sunshine

## Windows 安裝方式

1. 前往官方 Releases 頁面下載 `sunshine-windows-installer.exe`

   https://github.com/LizardByte/Sunshine/releases

2. 執行安裝程式，按照畫面提示一直點選下一步完成安裝。

3. 安裝完成後，在 Windows 程式列表搜尋 `Sunshine` 並開啟。

4. Sunshine 開啟後，正常情況下會顯示在系統匣。

5. 可以透過以下其中一種方式開啟 Sunshine 後台：

   - 在系統匣右鍵 Sunshine 圖示，選擇開啟 Sunshine
   - 或者直接開啟瀏覽器，輸入：

   ```text
   https://localhost:47990

6. 第一次開啟 Sunshine 後台時，系統會要求設定後台的帳號和密碼。

7. Windows UAC / 防火牆可能會詢問是否允許 Sunshine 通過防火牆，請選擇允許。

---

## macOS 安裝方式

以下安裝環境為：

* Mac Mini M4
* macOS Sequoia 15.7.1

其他 macOS 版本的安裝方式大致相同。

---

### 安裝 Homebrew

如尚未安裝 Homebrew，請先在 Terminal 執行以下指令：

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

---

### 配置 Homebrew 環境變數

請將 `<username>` 更換為你的 macOS 使用者名稱。

```bash
echo >> /Users/<username>/.zprofile
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/<username>/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

---

### 安裝 Sunshine

在 Terminal 執行以下指令：

```bash
brew tap LizardByte/homebrew
brew install sunshine
```

如果看到以下訊息，代表 Sunshine 已成功安裝：

```text
Thanks for installing Sunshine!
```

---

### 啟動 Sunshine

安裝完成後，在 Terminal 輸入：

```bash
sunshine
```

第一次執行時，macOS 可能會要求授權，請允許 Terminal 錄製此電腦畫面和音訊。

啟動後，Terminal 內會顯示 Sunshine 後台網址，例如：

```text
https://localhost:47990
```

開啟瀏覽器並輸入該網址。

第一次登入時，Sunshine 會要求設定 Username 和 Password。

---

### 安裝 Sunshine 開機啟動服務

如需要讓 Sunshine 以服務方式啟動，可以執行：

```bash
brew services start lizardbyte/homebrew/sunshine
```

---

### 安裝 BlackHole 音訊驅動

目前在 macOS 上，如果 Sunshine 沒有聲音，需要安裝 BlackHole。

```bash
brew install blackhole-2ch
```

安裝完成後，可在 macOS 音訊設定中檢查 BlackHole 2ch 是否可用。

---

### 解除安裝 Sunshine

如需解除安裝 Sunshine，可以執行：

```bash
brew uninstall sunshine
```

---

## 透過 VPN 遠端連線 Sunshine

如果需要在外部網絡使用 Moonlight 連接 Sunshine，建議使用 VPN，例如 Tailscale 或 ZeroTier。

這樣可以避免直接把 Sunshine 的端口開放到公網，安全性會比較好。

常見使用方式：

- Sunshine 安裝在被控制的電腦上，例如 Windows PC / Mac Mini
- Moonlight 安裝在客戶端裝置上，例如 Notebook / 手機 / 平板
- Sunshine 主機和 Moonlight 客戶端都加入同一個 VPN 網絡
- Moonlight 使用 VPN IP 連接 Sunshine 主機

---

## 方法一：使用 Tailscale

Tailscale 比較容易設定，適合一般使用。

官方下載頁面：

https://tailscale.com/download

官方安裝說明：

https://tailscale.com/docs/install

### Windows 安裝 Tailscale

1. 前往 Tailscale 官方下載頁面：

   ```text
   https://tailscale.com/download

2. 下載並安裝 Windows 版本 Tailscale。

3. 安裝完成後，開啟 Tailscale。

4. 使用同一個帳號登入，例如 Google / Microsoft / GitHub。

5. 登入後，Windows 電腦會取得一個 Tailscale IP，通常是：

   ```text
   100.x.x.x
   ```

6. 這台 Windows 電腦就是 Sunshine Host。

---

### macOS 安裝 Tailscale

可以直接到官方網站下載 macOS App：

```text
https://tailscale.com/download
```

或者使用 Homebrew 安裝：

```bash
brew install --cask tailscale
```

安裝完成後：

1. 開啟 Tailscale
2. 使用同一個帳號登入
3. 確認裝置已經出現在 Tailscale Admin Console

Tailscale Admin Console：

```text
https://login.tailscale.com/admin/machines
```

---

### 在 Moonlight 使用 Tailscale IP 連接 Sunshine

1. 確認 Sunshine 主機和 Moonlight 客戶端都已連接 Tailscale。

2. 在 Sunshine 主機查看 Tailscale IP，例如：

   ```text
   100.100.100.10
   ```

3. 在 Moonlight 客戶端選擇新增電腦。

4. 輸入 Sunshine 主機的 Tailscale IP：

   ```text
   100.100.100.10
   ```

5. Moonlight 會要求配對，畫面會顯示 PIN Code。

6. 開啟 Sunshine 後台：

   ```text
   https://localhost:47990
   ```

7. 在 Sunshine 後台輸入 Moonlight 顯示的 PIN Code 完成配對。

---

## 方法二：使用 ZeroTier

ZeroTier 也可以做到類似效果，但需要先建立一個 ZeroTier Network。

官方下載頁面：

```text
https://www.zerotier.com/download/
```

官方 Quickstart：

```text
https://docs.zerotier.com/quickstart/
```

---

### 建立 ZeroTier Network

1. 前往 ZeroTier Central：

   ```text
   https://my.zerotier.com/
   ```

2. 登入帳號。

3. 選擇 Create A Network。

4. 建立完成後，複製 Network ID，例如：

   ```text
   d5e04297a16fa690
   ```

---

### Windows / macOS 加入 ZeroTier Network

1. 安裝 ZeroTier。

2. 在 Windows 系統匣或 macOS Menu Bar 找到 ZeroTier 圖示。

3. 選擇：

   ```text
   Join New Network
   ```

4. 輸入你的 Network ID：

   ```text
   d5e04297a16fa690
   ```

5. 回到 ZeroTier Central：

   ```text
   https://my.zerotier.com/
   ```

6. 進入剛剛建立的 Network。

7. 在 Members 裡面找到新加入的裝置。

8. 勾選 Authorize，允許該裝置加入 VPN 網絡。

9. 裝置成功加入後，會取得一個 ZeroTier IP，例如：

   ```text
   10.147.17.20
   ```

---

### 使用指令加入 ZeroTier Network

如果需要使用 Terminal / CMD 加入，可以使用：

```bash
sudo zerotier-cli join <network-id>
```

例如：

```bash
sudo zerotier-cli join d5e04297a16fa690
```

成功後會看到類似：

```text
200 join OK
```

之後仍然需要到 ZeroTier Central 的 Members 頁面勾選 Authorize。

---

### 在 Moonlight 使用 ZeroTier IP 連接 Sunshine

1. 確認 Sunshine 主機和 Moonlight 客戶端都已加入同一個 ZeroTier Network。

2. 到 ZeroTier Central 查看 Sunshine 主機的 ZeroTier IP，例如：

   ```text
   10.147.17.20
   ```

3. 在 Moonlight 客戶端新增電腦。

4. 輸入 Sunshine 主機的 ZeroTier IP：

   ```text
   10.147.17.20
   ```

5. Moonlight 會顯示 PIN Code。

6. 開啟 Sunshine 後台：

   ```text
   https://localhost:47990
   ```

7. 在 Sunshine 後台輸入 PIN Code 完成配對。

---

## 注意事項

* Sunshine 不建議直接開端口到公網。

* 建議只透過 Tailscale 或 ZeroTier 的 VPN IP 連線。

* Sunshine 後台網址仍然是：

  ```text
  https://localhost:47990
  ```

* Moonlight 連線時，請使用 VPN IP，不要使用 `localhost`。

* `localhost` 只代表目前這台電腦本機。

* 如果 Moonlight 找不到 Sunshine 主機，可以手動輸入 VPN IP。

* 確認 Windows 防火牆已允許 Sunshine 通過。

* 確認 Sunshine 主機和 Moonlight 客戶端都在線上，並且在同一個 VPN 網絡內。




