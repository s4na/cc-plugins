---
name: playwright-cli
description: Playwright CLIを使ってブラウザ操作を自動実行するスキル。MCP Serverよりトークン効率が良く、シェルから直接ブラウザ操作が可能です。
---

# Playwright CLI Skill

Playwright MCP Server v0.0.58 で追加された Playwright CLI を使ってブラウザ操作を自動実行するスキルです。

## Playwright CLI とは

Playwright CLI は @playwright/mcp パッケージに含まれる CLI ツールで、MCP サーバー経由よりもトークン効率が良くブラウザ操作が可能です。要素の参照には snapshot で取得した ref を使用します。

## 前提条件

このスキルを使用するには、@playwright/mcp がグローバルインストールされている必要があります。

```bash
npm install -g @playwright/mcp@latest
```

インストール確認：
```bash
playwright-cli --help
```

## 主要コマンド

### Core（基本操作）

| コマンド | 説明 | 例 |
|----------|------|-----|
| `open <url>` | URLを開く | `playwright-cli open https://example.com` |
| `close` | ページを閉じる | `playwright-cli close` |
| `snapshot` | ページスナップショットを取得（要素ref取得用） | `playwright-cli snapshot` |
| `click <ref>` | 要素をクリック | `playwright-cli click e8` |
| `fill <ref> <text>` | テキスト入力 | `playwright-cli fill e8 "Hello"` |
| `type <text>` | 編集可能な要素にテキスト入力 | `playwright-cli type "Hello"` |
| `hover <ref>` | 要素にホバー | `playwright-cli hover e8` |
| `select <ref> <val>` | ドロップダウンを選択 | `playwright-cli select e8 "option1"` |
| `check <ref>` | チェックボックスをチェック | `playwright-cli check e8` |
| `uncheck <ref>` | チェックボックスを解除 | `playwright-cli uncheck e8` |
| `upload <file>` | ファイルアップロード | `playwright-cli upload file.txt` |
| `drag <startRef> <endRef>` | ドラッグ＆ドロップ | `playwright-cli drag e8 e10` |
| `eval <func> [ref]` | JavaScriptを実行 | `playwright-cli eval "document.title"` |
| `resize <w> <h>` | ウィンドウサイズ変更 | `playwright-cli resize 1280 720` |

### Navigation（ナビゲーション）

| コマンド | 説明 |
|----------|------|
| `go-back` | 前のページに戻る |
| `go-forward` | 次のページに進む |
| `reload` | ページをリロード |

### Keyboard（キーボード）

| コマンド | 説明 | 例 |
|----------|------|-----|
| `press <key>` | キーを押す | `playwright-cli press Enter` |
| `keydown <key>` | キーを押し下げる | `playwright-cli keydown Shift` |
| `keyup <key>` | キーを離す | `playwright-cli keyup Shift` |

### Mouse（マウス）

| コマンド | 説明 | 例 |
|----------|------|-----|
| `mousemove <x> <y>` | マウス移動 | `playwright-cli mousemove 100 200` |
| `mousedown [button]` | マウスボタン押下 | `playwright-cli mousedown left` |
| `mouseup [button]` | マウスボタン離す | `playwright-cli mouseup` |
| `mousewheel <dx> <dy>` | スクロール | `playwright-cli mousewheel 0 100` |

### Save as（保存）

| コマンド | 説明 | 例 |
|----------|------|-----|
| `screenshot [ref]` | スクリーンショット | `playwright-cli screenshot` |
| `pdf` | PDFとして保存 | `playwright-cli pdf` |

### Tabs（タブ管理）

| コマンド | 説明 |
|----------|------|
| `tab-list` | タブ一覧 |
| `tab-new [url]` | 新しいタブを開く |
| `tab-close [index]` | タブを閉じる |
| `tab-select <index>` | タブを選択 |

### DevTools（開発者ツール）

| コマンド | 説明 |
|----------|------|
| `console [min-level]` | コンソールメッセージ一覧 |
| `network` | ネットワークリクエスト一覧 |
| `run-code <code>` | Playwrightコードスニペット実行 |
| `tracing-start` | トレース記録開始 |
| `tracing-stop` | トレース記録停止 |

### Sessions（セッション管理）

| コマンド | 説明 |
|----------|------|
| `session-list` | セッション一覧 |
| `session-stop [name]` | セッション停止 |
| `session-stop-all` | 全セッション停止 |
| `session-delete [name]` | セッションデータ削除 |

### Dialog（ダイアログ）

| コマンド | 説明 |
|----------|------|
| `dialog-accept [prompt]` | ダイアログを承認 |
| `dialog-dismiss` | ダイアログを閉じる |

## 使い方

### Step 1: インストール確認

```bash
playwright-cli --help
```

**インストールされていない場合は、以下のメッセージを表示して処理を終了してください：**

```
playwright-cli がインストールされていません。

以下のコマンドでインストールしてください：
npm install -g @playwright/mcp@latest
```

### Step 2: 基本的なフロー

1. ページを開く
2. スナップショットで要素を特定
3. 要素を操作
4. 結果を確認
5. ブラウザを閉じる

## 実行例

### 例1: TodoMVCのテスト

```bash
# ページを開く
playwright-cli open https://demo.playwright.dev/todomvc

# スナップショットで要素のrefを確認
playwright-cli snapshot

# 入力フィールドにテキストを入力（refはsnapshotで確認）
playwright-cli fill e8 "新しいタスク"

# Enterキーを押して追加
playwright-cli press Enter

# 結果を確認
playwright-cli snapshot

# ブラウザを閉じる
playwright-cli close
```

### 例2: ログインフロー

```bash
# ログインページを開く
playwright-cli open https://example.com/login

# スナップショットで要素確認
playwright-cli snapshot

# ユーザー名入力
playwright-cli fill e10 "username"

# パスワード入力
playwright-cli fill e12 "password"

# ログインボタンクリック
playwright-cli click e15

# 結果確認
playwright-cli snapshot

# 閉じる
playwright-cli close
```

### 例3: スクリーンショット取得

```bash
playwright-cli open https://example.com
playwright-cli screenshot
playwright-cli close
```

## agent-browser との違い

| 項目 | playwright-cli | agent-browser |
|------|---------------|---------------|
| パッケージ | @playwright/mcp | agent-browser |
| ベース | Playwright | Puppeteer |
| スナップショット | YAMLファイルに保存 | 標準出力 |
| セッション管理 | session-* コマンド | --session オプション |
| トレース | tracing-start/stop | なし |

## スナップショットファイル

`playwright-cli snapshot` を実行すると、`.playwright-cli/` ディレクトリにYAMLファイルが作成されます。このファイルには要素の ref（例: e8, e10）が含まれており、これを使って要素を操作します。

## 注意事項

- スナップショットは操作のたびに取得して最新の状態を確認することを推奨
- ref は動的に変わる可能性があるため、操作前に必ず snapshot で確認する
- 複数タブを使う場合は tab-select でアクティブタブを切り替える
- 認証情報などの機密データの取り扱いに注意
