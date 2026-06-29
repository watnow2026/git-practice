# Gitチーム開発フロー実践

このレポジトリは、サークルの新入生がチーム開発のGitフローを実際に練習するための教材です。

読むよりも、手を動かして覚えることを目的にしています。

## 今日やること

1. `main` を最新にする
2. 自分の作業ブランチを作る
3. 自己紹介ファイルを追加する
4. commitする
5. 自分のブランチにpushする
6. Pull Requestを作る
7. レビュー後にmergeしてもらう
8. コンフリクト解消を練習する

## 絶対に守ること

`main` に直接pushしないでください。

NG:

```bash
git push origin main
```

チーム開発では、自分の作業ブランチにpushしてからPull Requestを作ります。

## 使うコマンド

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

コンフリクトが起きた場合:

```bash
git checkout コンフリクトしたブランチ名
git merge main

# コンフリクト箇所を修正

git add .
git commit -m "modify conflict"
git push origin コンフリクトしたブランチ名
```

実習の詳しい進め方は [docs/workshop.md](docs/workshop.md) を見てください。

