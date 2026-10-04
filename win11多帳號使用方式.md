# ① 建立三個 Claude 帳號資料夾

開啟 PowerShell：

```sh
New-Item -ItemType Directory -Force -Path "C:\ClaudeProfiles\Account-A"
New-Item -ItemType Directory -Force -Path "C:\ClaudeProfiles\Account-B"
New-Item -ItemType Directory -Force -Path "C:\ClaudeProfiles\Account-C"
```

會得到：

```
C:\ClaudeProfiles\
├── Account-A
├── Account-B
└── Account-C
```

# ② 建立 Claude A 啟動器

在桌面建立：

```sh
Claude-A.bat
```

內容：

```bat
@echo off
title Claude Code - Account A

set "CLAUDE_CONFIG_DIR=C:\ClaudeProfiles\Account-A"

cd /d "D:\Project_A"

claude
pause
```

例如你的專案是：

```
D:\GitHub\ProjectA
```

就改成：

```bat
cd /d "D:\GitHub\ProjectA"
```

# ③ 建立 Claude B

建立：

```sh
Claude-B.bat
```

內容：

```bat
@echo off
title Claude Code - Account B

set "CLAUDE_CONFIG_DIR=C:\ClaudeProfiles\Account-B"

cd /d "D:\Project_B"

claude
pause
```

# ④ 建立 Claude C

建立：

```sh
Claude-C.bat
```

內容：

```bat
@echo off
title Claude Code - Account C

set "CLAUDE_CONFIG_DIR=C:\ClaudeProfiles\Account-C"

cd /d "D:\Project_C"

claude
pause
```

# ⑤ 第一次分別登入

這一步很重要。

先雙擊

```sh
Claude-A.bat
```

第一次會要求登入。

登入：

```sh
Claude 帳號 A
```

登入完成後：

```sh
/status
```

確認目前帳號。

Claude Code 官方 CLI 有 `/status` 等相關狀態資訊，而 `/login`、`/logout` 也仍是官方命令。

## 接著開 Claude-B.bat

會是另一個獨立環境：

C:\ClaudeProfiles\Account-B

登入：

```sh
Claude 帳號 B
```

## 再開 Claude-C.bat

登入：

```sh
Claude 帳號 C
```

# ⑥ 最後就可以三個同時跑

例如：

```
┌─────────────────────────────────┐
│ Claude Code - Account A         │
│ 帳號：A                          │
│ 專案：Project_A                  │
└─────────────────────────────────┘

┌─────────────────────────────────┐
│ Claude Code - Account B         │
│ 帳號：B                          │
│ 專案：Project_B                  │
└─────────────────────────────────┘

┌─────────────────────────────────┐
│ Claude Code - Account C         │
│ 帳號：C                          │
│ 專案：Project_C                  │
└─────────────────────────────────┘
```

三個 Claude Code 可以同時運作。

而且：

```sh
Account A
    ↓
C:\ClaudeProfiles\Account-A
    ↓
登入 A
    ↓
Project A


Account B
    ↓
C:\ClaudeProfiles\Account-B
    ↓
登入 B
    ↓
Project B
```

兩邊的登入狀態分開。官方文件也明確描述，為不同帳號指定不同 configuration directory，可以讓多個帳號保持登入。

⭐ 我更推薦你的做法

如果你是拿 Claude Code 寫程式，我會做成：

```sh
C:\ClaudeProfiles\
│
├── Personal\
│    └── Claude 個人帳號
│
├── Work\
│    └── Claude 工作帳號
│
└── Coding\
     └── Claude 第三帳號
```

然後桌面：

```
🟢 Claude Personal
🔵 Claude Work
🟣 Claude Coding
```

雙擊就直接進對應專案。

例如：

```sh
Claude Personal
     ↓
D:\GitHub\MyProject
     ↓
Account A


Claude Work
     ↓
D:\GitHub\CompanyProject
     ↓
Account B


Claude Coding
     ↓
D:\GitHub\AIProject
     ↓
Account C
```
