# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## プロジェクト概要

これはNext.js 15を使用したテンプレートプロジェクトです。多言語対応（next-intl）、UIコンポーネント（shadcn/ui）、状態管理（jotai）を備えています。

## 開発コマンド

```bash
# 開発サーバーの起動（Turbopackを使用）
npm run dev

# ビルド前にPrettierで形式チェック
npm run prebuild

# プロダクションビルド
npm run build

# プロダクションサーバーの起動
npm start

# リンターの実行
npm run lint

# コードフォーマット
npm run format
```

## プロジェクト構造

### アプリケーションアーキテクチャ

1. **ルーティング**: Next.js App Routerを使用し、`[locale]`ディレクトリで多言語対応
2. **国際化**: next-intlを使用（en/jaをサポート、デフォルトは英語）
3. **スタイリング**: Tailwind CSS v4 + shadcn/ui
4. **状態管理**: Jotaiを使用
5. **型安全性**: TypeScript（strict mode有効）

### ディレクトリ構造の規則

- `src/app/[locale]/`: ロケール別のページコンポーネント
- `src/app/[locale]/(components)/`: 特定の画面専用のコンポーネント
- `src/components/common/`: 複数画面で使用する共通コンポーネント
- `src/components/ui/`: shadcn/uiのコンポーネント
- `src/stores/`: Jotaiのアトム定義
- `src/hooks/`: カスタムフック
- `src/lib/`: 共通ユーティリティ
- `messages/`: 多言語化用のJSONファイル

### 重要な設定

1. **TypeScript**: パスエイリアス `@/*` を `./src/*` に設定
2. **Volta**: Node.js 20.19.3で固定
3. **ESLint + Prettier**: コード品質の自動チェック

## 開発ガイドライン

1. **関数定義**: アロー関数を使用すること
2. **コンポーネント配置**:
   - 画面固有のコンポーネントは`app/[locale]/(components)/`に配置
   - 共通コンポーネントは`src/components/common/`に配置
3. **国際化**:
   - メッセージはページ単位で管理（例：`home.json`はホームページ用）
   - 共通コンポーネントで使用するメッセージは`common.json`に追加
   - 新しいページを作成する場合は対応するメッセージファイルを作成
4. **スタイリング**: Tailwind CSSとshadcn/uiを優先使用

## 新機能実装時の手順

1. 関連するメッセージを`messages/`に追加
2. 必要に応じてJotaiのアトムを`src/stores/`に定義
3. コンポーネントを適切なディレクトリに作成
4. `npm run lint`でコードチェック
5. `npm run format`でフォーマット

## 注意事項

- 技術スタックのバージョンは変更しないこと
- UIデザインの変更は事前承認が必要
- 既存のディレクトリ構造を厳守すること
