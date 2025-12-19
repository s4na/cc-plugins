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
| `/code-review [対象]` | 複数のサブエージェントを並列実行して包括的なコードレビューを行います |

### /code-review

複数の専門サブエージェントを並列で起動し、以下の観点から包括的なコードレビューを実施します：

- **設計レビュー**: SOLID原則、デザインパターン、依存関係の適切性
- **品質レビュー**: 命名規則、可読性、DRY原則
- **セキュリティレビュー**: OWASP Top 10、認証・認可
- **パフォーマンスレビュー**: N+1クエリ、不要な再レンダリング
- **保守性レビュー**: テスタビリティ、拡張性
- **テストレビュー**: テストの品質・網羅性

**使用例:**
```bash
/code-review                    # 現在のブランチの変更をレビュー
/code-review src/utils/auth.ts  # 特定のファイルをレビュー
```