# 🧠 Claude Code CLI 安裝 SOP

## 🚀 安裝方式

🔹 官方腳本
▶ Windows（PowerShell）

```sh
irm https://claude.ai/install.ps1 | iex
```

▶ macOS / Linux / WSL

```sh
curl -fsSL https://claude.ai/install.sh | bash
```

👉 這是官方推薦方式，會自動安裝與更新

▶ 將系統加入環境變數

```sh
[Environment]::SetEnvironmentVariable(
  "Path",
  $env:Path + ";C:\Users\admin\.local\bin",
  [EnvironmentVariableTarget]::User
)
```

🔹 套件管理工具

Windows（winget）

```sh
winget install Anthropic.ClaudeCode
```

✅ 驗證安裝

```sh
claude --version
```

🔐 登入帳號

```sh
claude
```

然後輸入：

```sh
/login
```

👉 會自動開瀏覽器登入（支援 SSO）

🧪 測試 CLI 是否正常

```sh
claude "explain this project"
```

或：

```sh
claude -p "寫一個 python hello world"
```

👉 CLI 主要指令包含：

- claude → 互動模式
- claude -p → 單次指令模式
- claude update → 更新版本

🧩 進階（開發者必看）

▶ CLI 常用參數

```sh
claude --model sonnet
claude --verbose
claude --continue
```

▶ 管線操作（很強）

```sh
cat log.txt | claude -p "幫我分析錯誤"
```

👉 CLI 支援：

- pipe
- session resume
- 自動 agent 工作流

## claude code 使用 ollama models

$env:ANTHROPIC_AUTH_TOKEN="ollama"
$env:ANTHROPIC_API_KEY=""
$env:ANTHROPIC_BASE_URL="http://220.135.135.29:11436"
claude --model qwen3.5:9b
