## Todo Expo アプリ

Expo SDK 54 / React Native 0.81 ベースのシンプルな Todo アプリです。  
モバイル向けに、ダークトーンでモダンな UI とフィルター機能を備えています。

### 前提条件

- **Node.js**: 18 以上（LTS 推奨）
- **npm**: Node に同梱されているものを利用
- **Expo Go アプリ**
  - iOS / Android 実機にインストールしておくと QR コードからすぐに確認できます
- **Git**（任意）

### 主な技術スタック

- **Expo**: `~54.0.0`
- **React Native**: `0.81.x`
- **React**: `19.1.0`
- **TypeScript**

### セットアップ手順

1. リポジトリを取得

   ```bash
   cd /Users/yuito/work
   # すでにある場合は不要
   git clone <このプロジェクトのリポジトリURL> todo_expo
   cd todo_expo
   ```

2. 依存関係のインストール

   ```bash
   npm install
   ```

   もし依存関係の解決エラーが出る場合は、次のコマンドを試してください。

   ```bash
   npm install --legacy-peer-deps
   ```

### 開発サーバーの起動（モバイル / ネイティブ）

```bash
npm start
```

コマンド実行後に表示される QR コードを **Expo Go** で読み取るか、ターミナルのメニューから iOS シミュレータ / Android エミュレータを起動して動作確認します。

### Web 版の起動

Web 版をブラウザで確認する場合は、Web 用依存関係をインストールしたうえで起動します。

1. 必要なパッケージをインストール（初回のみ）

   ```bash
   npx expo install react-dom react-native-web
   ```

2. Web 開発サーバーの起動

   ```bash
   npm run web
   # または
   npx expo start --web
   ```

ブラウザが立ち上がり、同じ Todo アプリを Web アプリとして確認できます。  
スマホレイアウトを確認したい場合は、開発者ツールでスマホ表示を利用してください。

### プログラム構成の概要

- `App.tsx`
  - アプリ本体のロジックと UI がすべてまとまっているファイルです。
  - **状態管理**
    - `todos`: Todo の配列（`id`, `text`, `completed`）
    - `inputText`: 入力中のテキスト
    - `filter`: 表示フィルター（`all` / `active` / `completed`）
  - **主な関数**
    - `addTodo`: 新しいタスクを追加
    - `toggleTodo`: タスクの完了 / 未完了を切り替え
    - `deleteTodo`: タスクを削除
    - `getFilteredTodos`: フィルターに応じて表示するリストを計算
  - **UI 構成**
    - ヘッダー: 「TODAY / My Tasks」と未完了タスク数バッジ
    - フィルター: すべて / 未完了 / 完了 のチップボタン
    - タスクリスト: `FlatList` を使ったカード型表示
    - 入力エリア: テキスト入力＋「＋」ボタンで追加
- 設定ファイル
  - `package.json`: 依存関係と npm スクリプト（`npm start`, `npm run web` など）
  - `app.json`: Expo のアプリ設定（名前・バージョン・プラットフォーム設定など）
  - `tsconfig.json`: TypeScript の設定（型チェック・モジュール解決）
  - `babel.config.js`: Babel の設定（Expo 用プリセットの指定）

### 実装されている主な機能

- **タスクの追加**: 画面下部の入力欄＋「＋」ボタン、またはキーボードの Enter で追加
- **タスクの完了/未完了切り替え**: タスク行の左側の丸いチェックをタップ
- **タスクの削除**: 右端の「×」ボタンをタップ
- **フィルター機能**:
  - すべて
  - 未完了
  - 完了
- **UI/UX**
  - ダークテーマ
  - 残りタスク数バッジ
  - カード型のタスク表示
  - モバイル向けの余白とタップしやすいサイズ

### よくあるトラブル

- **Expo Go と SDK バージョンの不一致**
  - App Store / Google Play の Expo Go は基本的に最新 SDK 向けです
  - このプロジェクトは **SDK 54** 向けなので、Expo Go も SDK 54 対応版である必要があります

不明点やエラーが出た場合は、ターミナルのログと一緒に質問してください。***


