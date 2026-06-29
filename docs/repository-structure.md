# レポジトリ内の基本構成

この資料では、よくあるレポジトリのディレクトリ構成を説明します。

Gitの操作手順ではなく、「どこに何が入るのか」を確認するための資料です。

## よくある構成例

```text
repository-name/
├── README.md
├── docs/
├── backend/
├── frontend/
├── scripts/
├── .github/
├── .gitignore
└── package.json など
```

すべてのレポジトリに必ず同じディレクトリがあるわけではありません。プロジェクトの種類によって、名前や数は変わります。

## ルートディレクトリ

レポジトリを開いた直後に見える一番上の場所です。

よく置かれるもの:

- `README.md`
- `.gitignore`
- `.github/`
- `docs/`
- `backend/`
- `frontend/`
- 設定ファイル

ルートには、プロジェクト全体に関係するファイルを置きます。

## README.md

レポジトリの入口になる説明ファイルです。

よく書かれる内容:

- このプロジェクトが何をするものか
- セットアップ方法
- 開発の始め方
- よく使うコマンド
- 関連ドキュメントへのリンク

初めてレポジトリを開いたら、まず `README.md` を読みます。

## docs/

ドキュメントを置くディレクトリです。

よく入るもの:

- 開発手順
- 仕様メモ
- 設計メモ
- 運用手順
- 学習用資料
- トラブルシューティング

コードではなく、人が読む説明を置く場所です。

## backend/

サーバー側のコードを置くディレクトリです。

よく入るもの:

- API
- データベース処理
- 認証処理
- 管理画面の処理
- バッチ処理

例:

```text
backend/
├── app/
├── config/
├── db/
└── tests/
```

Rails、Laravel、Django、Express、Go、Javaなど、使う技術によって中身は変わります。

## frontend/

ユーザーが見る画面側のコードを置くディレクトリです。

よく入るもの:

- 画面コンポーネント
- ページ
- CSS
- 画像などの静的ファイル
- フロントエンドのテスト

例:

```text
frontend/
├── src/
├── public/
├── package.json
└── tests/
```

React、Vue、Next.js、Nuxtなどを使う場合によく見ます。

## scripts/

開発や運用を楽にするためのスクリプトを置く場所です。

よく入るもの:

- セットアップ用スクリプト
- データ作成スクリプト
- デプロイ補助
- 確認用コマンド

実行すると何かが変わるスクリプトもあるため、初めて見るものは中身やREADMEを確認してから使います。

## .github/

GitHub用の設定を置くディレクトリです。

よく入るもの:

- Pull Requestテンプレート
- Issueテンプレート
- GitHub Actionsの設定

例:

```text
.github/
├── pull_request_template.md
└── workflows/
```

## .gitignore

Gitで管理しないファイルを指定するためのファイルです。

よく除外するもの:

- OSが作る一時ファイル
- エディタの個人設定
- ビルド結果
- ログ
- 秘密情報を含む `.env`

`.gitignore` に書かれているファイルは、通常 `git status` に出てこなくなります。

## 設定ファイル

プロジェクトの技術によって、ルートに設定ファイルが置かれます。

例:

- `package.json`
- `Gemfile`
- `requirements.txt`
- `pyproject.toml`
- `docker-compose.yml`
- `Makefile`

これらは、使うライブラリ、起動方法、開発環境などを定義します。

## この教材レポジトリの構成

この教材では、学習に必要なものだけを置いています。

```text
git-practice/
├── README.md
├── docs/
├── introductions/
├── practice/
├── .github/
└── .gitignore
```

- `README.md`: 教材の入口
- `docs/`: 実習手順や補足資料
- `introductions/`: 各自の自己紹介ファイルを追加する場所
- `practice/`: コンフリクト練習用ファイル
- `.github/`: Pull Requestテンプレート
- `.gitignore`: Gitで管理しないファイルの指定

## 迷ったときの見方

初めてのレポジトリでは、次の順番で見ると理解しやすいです。

1. `README.md` を読む
2. `docs/` があれば見る
3. `backend/` と `frontend/` があるか確認する
4. `.github/` でPRやCIのルールを確認する
5. `.gitignore` で管理しないファイルを確認する
