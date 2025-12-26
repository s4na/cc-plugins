# cc-plugins

Claude Code用のカスタムスラッシュコマンド集です。

## マーケットプレイスの追加方法

Claude Codeで以下のコマンドを実行してマーケットプレイスを追加します：

```bash
/plugin marketplace add s4na/cc-plugins
```

追加後、プラグインをインストールできます：

```bash
/plugin install hoge@cc-plugins
```

### 手動インストール

このリポジトリの `.claude/commands/` ディレクトリ内のコマンドを、あなたのプロジェクトの `.claude/commands/` にコピーしてください。

## アンインストール方法

プラグインをアンインストールするには：

```bash
/plugin uninstall hoge
```

マーケットプレイス自体を削除するには：

```bash
/plugin marketplace remove cc-plugins
```

## 利用可能なコマンド

| コマンド | 説明 |
|---------|------|
| `/hoge` | "hoge" と返します |
| `/himari <テキスト>` | VOICEVOXのhimari(冥鳴ひまり)でテキストを音声読み上げします |

## 利用可能なサブエージェント

サブエージェントは `.claude/agents/` ディレクトリに配置します。

| サブエージェント | 説明 |
|-----------------|------|
| `prompt-engineer` | サブエージェント向けプロンプトを最適化するエージェント |

### サブエージェントの手動インストール

このリポジトリの `.claude/agents/` ディレクトリ内のファイルを、あなたのプロジェクトの `.claude/agents/` にコピーしてください。