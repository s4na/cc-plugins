# cc-plugins

[![hoge version](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fs4na%2Fcc-plugins%2Fmain%2F.claude-plugin%2Fmarketplace.json&query=%24.plugins%5B0%5D.version&label=hoge&color=blue)](https://github.com/s4na/cc-plugins)
[![basic version](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fs4na%2Fcc-plugins%2Fmain%2F.claude-plugin%2Fmarketplace.json&query=%24.plugins%5B1%5D.version&label=basic&color=green)](https://github.com/s4na/cc-plugins)

Claude Code用のカスタムスラッシュコマンド集です。

## インストール方法

### マーケットプレイス経由（推奨）

Claude Codeで以下のコマンドを実行してマーケットプレイスを追加します：

```bash
/plugin marketplace add s4na/cc-plugins
```

追加後、プラグインをインストールできます：

hogeプラグイン（シンプルなサンプル）
```bash
/plugin install hoge@cc-plugins
```

basicプラグイン（便利なコマンド集）
```bash
/plugin install basic@cc-plugins
```

### 手動インストール

- **hogeプラグイン**: `.claude/` ディレクトリをコピー
- **basicプラグイン**: `.claude-basic/` ディレクトリを `.claude/` としてコピー

## アンインストール方法

プラグインをアンインストールするには：

```bash
/plugin uninstall hoge
```
```bash
/plugin uninstall basic
```

マーケットプレイス自体を削除するには：

```bash
/plugin marketplace remove cc-plugins
```

## 利用可能なプラグイン

### hoge プラグイン

シンプルなサンプルプラグインです。

| コマンド | 説明 |
|---------|------|
| `/hoge` | "hoge" と返します |

### basic プラグイン

便利なコマンドとサブエージェントをまとめたプラグインです。

#### コマンド

| コマンド | 説明 |
|---------|------|
| `/himari <テキスト>` | VOICEVOXのhimari(冥鳴ひまり)でテキストを音声読み上げします |
| `/manager <依頼内容>` | マネージャーモードで作業を全てサブエージェントに委譲します |
| `/browser <依頼内容>` | Playwright MCPを使ってブラウザ操作を実行します |
| `/ask <質問>` | AskUserQuestionツールを使ってユーザーに質問を投げかけます |

#### スキル

| スキル | 説明 |
|--------|------|
| `codex` | Codex CLIを使ってコードレビュー・分析を自動実行します |

#### サブエージェント

| サブエージェント | 説明 |
|-----------------|------|
| `prompt-engineer` | サブエージェント向けプロンプトを最適化するエージェント |
| `browser-operator` | Playwright MCPでブラウザ操作を実行するエージェント |
