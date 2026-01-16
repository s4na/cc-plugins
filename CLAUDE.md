# CLAUDE.md

このプロジェクトはClaude Codeプラグインのマーケットプレイスです。

## バージョン管理ルール

プラグインを更新した場合は、**必ずパッチバージョンを1ずつインクリメント**してください。

### 対象ファイル
`.claude-plugin/marketplace.json` の各プラグインの `version` フィールド

### ルール
- プラグインに変更を加えたら、そのプラグインの `version` をインクリメントする
- セマンティックバージョニング（SemVer）に従う: `MAJOR.MINOR.PATCH`
- 通常の修正・機能追加は PATCH バージョンをインクリメント（例: `1.0.0` → `1.0.1`）
- 破壊的変更がある場合は MINOR または MAJOR を更新

### 例
`basic` プラグインを更新した場合:
```json
{
  "name": "basic",
  "version": "1.0.0"  // 変更前
}
↓
{
  "name": "basic",
  "version": "1.0.1"  // 変更後
}
```

## スキル作成ルール

スキルを作成する場合は、`npx add-skill` に対応する形式で作成してください。

### ディレクトリ構造
```
.claude-basic/skills/
  <スキル名>/
    SKILL.md    ← 必須
```

### SKILL.md の形式
ファイル名は必ず `SKILL.md`（大文字）にしてください。

```markdown
---
name: <スキル名>
description: <スキルの説明>
---

# <スキル名>

<スキルの詳細な説明と使い方>
```

### 必須要素
- **frontmatter**: `---` で囲んだ YAML 形式のメタデータ
  - `name`: スキルの識別子（小文字、ハイフン使用可）
  - `description`: スキルの簡潔な説明
- **本文**: スキルの詳細な説明、使い方、実行手順など

### 例
`codex` スキルの場合:
```
.claude-basic/skills/
  codex/
    SKILL.md
```

```markdown
---
name: codex
description: Codex CLIを使ってコードレビュー・分析を自動実行するスキル
---

# Codex Skill

Codex CLIを使ってコードレビュー・分析を実行するスキルです。
...
```

### 確認方法
スキル作成後、以下のコマンドで認識されることを確認してください:
```bash
npx add-skill s4na/cc-plugins --list
```
