# VARGG MCP

[![MCP Protocol](https://img.shields.io/badge/MCP-Protocol-blue)](https://modelcontextprotocol.io)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Discussions](https://img.shields.io/badge/discussions-welcome-blue)](https://github.com/var-gg/mcp/discussions)

**Languages / 语言 / 言語 / 언어 / Ngôn ngữ:**
- [![English](https://img.shields.io/badge/English-Click-yellow)](README.md)
- [![한국어](https://img.shields.io/badge/한국어-클릭-yellow)](README-ko.md)
- [![日本語](https://img.shields.io/badge/日本語-クリック-blue)](README-ja.md)
- [![简体中文](https://img.shields.io/badge/简体中文-点击查看-orange)](README-zh.md)
- [![Tiếng Việt](https://img.shields.io/badge/Tiếng_Việt-Nhấn_vào-green)](README-vi.md)

> **Model Context Protocolによるプロジェクトメタデータ管理ツール**

プロジェクトごとに変数名、定数、標準用語を体系的に管理し、Cursor IDEと統合してLLMが一貫した命名規則を使用できるようにします。

---

## 🎯 概要

VARGG MCPは、開発環境と一元化されたプロジェクトメタデータ管理システム間のシームレスな統合を可能にするModel Context Protocolの実装です。特にCursor IDEなどのAIアシスタントで作業する際に、プロジェクト全体で一貫した命名規則を維持するのに役立ちます。

### 解決する問題

- **一貫性のない命名**: 開発者によって同じ概念に対して異なる変数名を使用
- **言語の壁**: 複数の言語で作業するチームが用語の一貫性を維持するのが困難
- **AIコンテキストの損失**: LLMがチームの確立された規則を知らずにコードを生成
- **知識の孤立**: プロジェクト固有の命名パターンが共有されていない、または発見されない
- **オンボーディングの摩擦**: 新しいチームメンバーがどの命名規則に従うべきかわからない

### 主な機能の概要

- **プロジェクトベースの組織**: プロジェクトごとに変数と定数を管理
- **多言語サポート**: 韓国語、英語、日本語、中国語、ベトナム語のネイティブサポート
- **Cursor IDE統合**: MCPプロトコルを通じたCursor IDEとの直接統合
- **リアルタイム検索**: 既存の変数と定義を即座に検索
- **標準用語**: プロジェクト全体で一貫した定義を維持
- **チーム協力**: チーム内で命名パターンを共有し、発見

### 対象ユーザー

- **開発チーム**: 一貫した命名規則を維持したいチーム
- **多言語プロジェクト**: 複数の言語とロケールを含むプロジェクト
- **AI支援開発**: Cursor IDEまたは類似のAIコーディングアシスタントを使用する開発者
- **プロジェクトマネージャー**: プロジェクト全体で標準化された用語を管理するチーム

---

## ✨ 主な機能

### 🗂️ プロジェクトベースの変数管理
変数と定数をプロジェクトごとに整理し、プロジェクト固有の命名規則を簡単に維持しながら、チーム間で共通パターンを共有できます。

### 🌐 多言語サポート
5つの言語を完全サポート:
- 🇰🇷 韓国語 (ko)
- 🇺🇸 英語 (en)
- 🇯🇵 日本語 (ja)
- 🇨🇳 中国語 (zh)
- 🇻🇳 ベトナム語 (vi)

各言語は、変数名と定義に対する独自の検証規則と文字セットを持っています。

### 🔌 Cursor IDE統合
Model Context Protocolを通じたCursor IDEとのシームレスな統合。LLMがコードを生成する際、チームの標準用語を自動的に検索して使用できます。

### 🔍 自動標準用語検索と提案
LLMがコードを生成する際、プロジェクトの変数ライブラリを検索し、新しいものを作成する代わりに既存の標準用語を提案します。

### ⚡ リアルタイム変数検索と登録
既存の変数を即座に検索し、作業中に新しい変数を登録します。すべての操作はMCPプロトコルを通じてリアルタイムで実行されます。

---

## 🚀 クイックスタート

### 前提条件

- Cursor IDEがインストールされていること
- VARGGアカウント ([var.gg](https://var.gg)で作成)
- VARGGウェブサイトからのAPIキー

### 1. APIキーを取得

1. [var.gg](https://var.gg)にアクセスしてログイン
2. アカウント設定に移動
3. MCPアクセス用のAPIキーを生成

### 2. Cursor IDEを設定

Cursor IDE設定にVARGG MCPを追加:

**ファイル(F) > 設定 > Cursor設定**

次の設定を追加:

```json
{
  "mcpServers": {
    "vargg": {
      "url": "https://var.gg/mcp/ja/project",
      "headers": {
        "X-API-KEY": "your-api-key-here"
      }
    }
  }
}
```

**注意**: `ja`を希望するロケール(`en`, `ko`, `zh`, `vi`)に置き換えてください。

ステップ1で取得した実際のAPIキーで`your-api-key-here`を置き換えてください。

### 3. 最初のプロジェクトを作成

Cursor IDEでAIアシスタントに依頼:

```
説明「Eコマースプラットフォーム用の支払い処理モジュール」で「E-Commerce Payment」という名前の新しいプロジェクトを作成
```

または、[var.gg/projects](https://var.gg/projects)のウェブインターフェースを使用してください。

### 4. 変数の使用を開始

Cursorに変数を検索または作成するよう依頼:

```
プロジェクトで「ユーザーアカウント」に関連する変数を検索
```

```
プロジェクトで定義「total count」の略語変数TOTAL_COUNTを作成
```

---

## 🛠️ 利用可能なツール

VARGG MCPは、プロジェクトと変数を管理するための次のツールを提供します:

### プロジェクト管理
- **`projects`** - アクセス可能なすべてのプロジェクトを一覧表示
- **`create_project`** - 新しいプロジェクトを作成
- **`update_project`** - プロジェクト情報を更新
- **`open_project_admin`** - 権限とユーザー招待のためのプロジェクト管理ページを開く

### 変数管理
- **`search_variables`** - プロジェクト内の変数を検索
- **`create_variables`** - プロジェクトに新しい変数を作成
- **`list_variables`** - プロジェクト内のすべての変数を一覧表示（ページネーション付き）
- **`remove_variables`** - プロジェクトから変数を削除

各ツールの詳細なドキュメントについては、[ツールリファレンス](docs/tools-reference.md)を参照してください。

---

## 📖 ドキュメント

- **[はじめに](docs/getting-started.md)** - 詳細なセットアップガイド
- **[ツールリファレンス](docs/tools-reference.md)** - すべてのツールの完全なAPIドキュメント
- **[Cursor統合ガイド](docs/integration-guide.md)** - ステップバイステップのCursor IDE設定
- **[ベストプラクティス](docs/best-practices.md)** - 推奨ワークフローとパターン
- **[使用例](examples/use-cases.md)** - 実際の例とシナリオ
- **[公式ウェブサイト](https://var.gg)** - インタラクティブなデモと詳細なガイド

---

## 💡 使用例

### チーム内の命名規則の統一
すべてのチームメンバーが共通の概念に対して同じ変数名を使用するようにします。たとえば、`UserAccount`、`userAccount`、`user_account`などを混在させる代わりに、常に`USER_ACCOUNT`を使用します。

### プロジェクトごとの標準用語の管理
各プロジェクトは独自の標準用語セットを持つことができます。「Payment」プロジェクトは`PAYMENT_AMOUNT`を持つことができ、「Shipping」プロジェクトは`SHIPPING_COST`を持つことができます。

### LLMコード生成の一貫性の確保
Cursorにコード生成を依頼すると、プロジェクトの変数ライブラリを検索し、既存の標準用語を使用して、生成されたすべてのコードで一貫性を維持します。

### 多言語プロジェクトの変数名管理
多言語サポートは、コードの英語変数名を維持しながら、母国語で変数を定義できることを意味します。たとえば、日本語定義「合計数」を持つ`TOTAL_COUNT`。

---

## 🤝 コミュニティ

- **[Issues](https://github.com/var-gg/mcp/issues)**: バグの報告、機能の提案、質問
- **[Discussions](https://github.com/var-gg/mcp/discussions)**: ヒントの共有、Q&A、アイデアの議論
- **ロードマップ**: 計画された機能と改善を確認（イシューラベルを確認）

### 貢献方法

1. [Discussions](https://github.com/var-gg/mcp/discussions)で使用例を共有
2. [Issues](https://github.com/var-gg/mcp/issues)を通じてバグを報告または機能をリクエスト
3. 「Show and Tell」カテゴリでベストプラクティスを共有

---

## 🌐 多言語サポート

VARGG MCPは、ネイティブ検証と文字セットを持つ次の言語をサポートします:

| Language | Code | Character Set |
|----------|------|---------------|
| 🇰🇷 韓国語 | `ko` | 한글 + 영문 + 숫자 + 공백 + 괄호 |
| 🇺🇸 英語 | `en` | English letters + numbers + spaces |
| 🇯🇵 日本語 | `ja` | ひらがな + カタカナ + 漢字 + 영문 + 숫자 |
| 🇨🇳 中国語 | `zh` | 汉字 + 영문 + 숫자 |
| 🇻🇳 ベトナム語 | `vi` | Vietnamese + 영문 + 숫자 |

各言語は、変数名と定義に対する特定の検証規則を持っています。詳細については、[ツールリファレンス](docs/tools-reference.md)を参照してください。

---

## 🔗 リンク

- **ウェブサイト**: [https://var.gg](https://var.gg)
- **MCPガイド**: [https://var.gg/ja/mcp](https://var.gg/ja/mcp) (en, ko, zh, viでも利用可能)
- **インタラクティブデモ**: [https://var.gg/[locale]/mcp](https://var.gg/ja/mcp) - ブラウザでツールを試す
- **イシュー報告**: [https://github.com/var-gg/mcp/issues](https://github.com/var-gg/mcp/issues)
- **ディスカッション**: [https://github.com/var-gg/mcp/discussions](https://github.com/var-gg/mcp/discussions)

---

## 📝 ライセンス

このプロジェクトはMITライセンスの下でライセンスされています - 詳細は[LICENSE](LICENSE)ファイルを参照してください。

---

## ⚠️ 重要な注意事項

### コードの公開

現在、このリポジトリにはドキュメントとコミュニティリソースのみが含まれています。MCPサーバーの実装コードはまだオープンソースではありませんが、将来公開する可能性があります。更新を確認してください！

### アーキテクチャの注意

VARGG MCP実装はJSON-RPC 2.0プロトコルインターフェースを使用します。Cursor IDEはJSON-RPC 2.0を使用してMCPサーバーと通信し、これはバックエンドへのREST API呼び出しに変換されます。フロントエンドは、CursorのMCPプロトコルとバックエンドREST API間のプロキシレイヤーとして機能します。

### バージョン管理

コードが公開されていなくても、[CHANGELOG.md](CHANGELOG.md)でMCPツールのバージョンと機能変更を追跡します。

### プライバシー

イシューを報告したり、機能について議論したりする際は、個人情報やAPIキーを共有しないでください。機密情報を共有する必要がある場合は、個人的に連絡してください。

---

**VARGGチームが ❤️ で作成しました**

