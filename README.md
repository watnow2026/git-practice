# Gitチーム開発 練習レポジトリ

このレポジトリは、サークルの新入生がチーム開発で使うGitの基本操作を練習するための教材です。

目的は次の3つです。

- `main` ブランチを直接変更しない流れを身につける
- 作業ブランチを作って、変更をコミットして、GitHubへpushする
- コンフリクトが起きたときに落ち着いて解消する

## 最初に覚えるルール

`main` ブランチに直接pushしてはいけません。

NG例:

```bash
git push origin main
```

理由:

`main` はチームの大元になるブランチです。直接pushすると、レビューを受けずに大元のソースコードを変更してしまいます。

チーム開発では、自分の作業ブランチにpushしてからPull Requestを作成します。

## 基本の作業フロー

作業を始める前は、必ず最新の `main` から作業ブランチを作ります。

```bash
git checkout main
git pull origin main
git checkout -b sho_dev
```

ファイルを編集したら、変更内容を確認します。

```bash
git status
```

変更したファイルをステージングします。

```bash
git add ファイル名
```

例:

```bash
git add introductions/sho.md
```

変更内容をコミットします。

```bash
git commit -m "add introduce"
```

自分の作業ブランチにpushします。

```bash
git push origin sho_dev
```

GitHub上でPull Requestを作成します。

## 全体の流れ

```bash
git checkout main
git pull origin main
git checkout -b 作業ブランチ名

# ファイルを編集

git status
git add .
git commit -m "変更内容がわかるメッセージ"
git push origin 作業ブランチ名
```

## コンフリクトを起こしにくくする手順

作業を始める前に、最新の `main` からブランチを作ることが大切です。

```bash
git checkout main
git pull origin main
git checkout -b sho_dev2

# ファイルを編集

git add ファイル名
git commit -m "hogehoge"
git push origin sho_dev2
```

## コンフリクトが起きた場合

コンフリクトが起きたブランチに移動します。

```bash
git checkout sho_dev2
```

最新の `main` を取り込みます。

```bash
git merge main
```

コンフリクトしているファイルを開くと、次のような表示があります。

```text
<<<<<<< HEAD
自分のブランチの変更内容
=======
mainブランチ側の変更内容
>>>>>>> main
```

残したい内容を選び、次の記号を削除します。

```text
<<<<<<< HEAD
=======
>>>>>>> main
```

修正後、ステージングしてコミットします。

```bash
git add .
git commit -m "modify conflict"
git push origin sho_dev2
```

GitHubのPull Request画面を確認し、`Conflicting files` の表示が消えていればコンフリクト解消完了です。

## この教材でやること

1. `introductions/` に自分の自己紹介ファイルを作る
2. `app/views/users/index.html.erb` を編集する
3. 作業ブランチにpushする
4. Pull Requestを作成する
5. 必要に応じてコンフリクト解消を練習する

詳しい実習手順は [docs/workshop.md](docs/workshop.md) を読んでください。

