# praxis

複数プロジェクトで共有する、Claude Code向けの共通スキル(プラグイン)を管理するリポジトリです。

このリポジトリ自体がClaude Codeの[プラグイン・マーケットプレイス](.claude-plugin/marketplace.json)であり、
`plugins/` 配下に各プラグインを配置しています。

## 提供プラグイン

| プラグイン | 内容 |
|---|---|
| [`praxis`](plugins/praxis) | 開発・運用におけるエージェントの普遍的な行動規範集(ワークフロー、ドキュメント執筆、UIモックアップ、ヘッドレスブラウザ操作) |

## 導入手順

Claude Code上で以下を実行します。

### 1. マーケットプレイスを登録する

```
/plugin marketplace add ng3rdstmadgke/praxis
```

ローカルにcloneしたリポジトリを直接指定する場合はパスを渡します。

```
/plugin marketplace add ./path/to/praxis
```

### 2. プラグインをインストールする

```
/plugin install praxis@praxis
```

インストール時にスコープ(ユーザー/プロジェクト/ローカル)を選択できます。

- **ユーザー**: `~/.claude/settings.json` に記録。すべてのプロジェクトで有効
- **プロジェクト**: `.claude/settings.json` に記録。バージョン管理され、チームで共有
- **ローカル**: `.claude/settings.local.json` に記録。このプロジェクトの自分だけ

### 3. 確認する

```
/plugin list
```

`praxis@praxis` が表示されていればインストール完了です。

## 更新する

マーケットプレイス側のリポジトリを更新した後、利用側で最新化する場合は再度マーケットプレイスを追加し直すか、
Claude Codeを再起動してください。

## リポジトリ構成

```
praxis/
├── .claude-plugin/
│   └── marketplace.json      # マーケットプレイス定義
└── plugins/
    └── praxis/
        ├── .claude-plugin/
        │   └── plugin.json   # praxisプラグインの定義
        └── skills/
            ├── project-workflow/         # 開発ワークフロー
            ├── cognitive-rhythm-writing/ # ドキュメント執筆
            ├── ui-mockup/                # UIモックアップ
            └── headless-browser-debug/   # ヘッドレスブラウザ操作・デバッグ
```

新しいプラグインを追加する場合は `plugins/` 配下にディレクトリを作成し、
`.claude-plugin/marketplace.json` の `plugins` 配列にエントリを追記してください。
