# cc-plugins

Claude Code用のカスタムスラッシュコマンド集です。

## インストール方法

### npx add-skill を使用（推奨）

[add-skill](https://github.com/vercel-labs/add-skill) を使って簡単にインストールできます。

スキル一覧を確認:
```bash
npx add-skill s4na/cc-plugins --list
```

全てのスキルをインストール:
```bash
npx add-skill s4na/cc-plugins
```

特定のスキルのみインストール:
```bash
npx add-skill s4na/cc-plugins --skill basic
```
```bash
npx add-skill s4na/cc-plugins --skill hoge
```

グローバルインストール（ユーザーディレクトリ）:
```bash
npx add-skill s4na/cc-plugins -g
```

### マーケットプレイス経由

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
