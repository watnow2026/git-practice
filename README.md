# Gitチーム開発フロー実践

このレポジトリは、サークルの新入生がチーム開発のGitフローを実際に練習するための教材です。

読むだけではなく、VS Code と GitHub を使って手を動かしながら進めます。

## 今日やること

1. `main` を最新にする
2. 自分の作業ブランチを作る
3. 自己紹介ファイルを追加する
4. 変更を確認する
5. commitする
6. 自分のブランチにpushする
7. Pull Requestを作る
8. レビュー後にmergeしてもらう
9. コンフリクト解消を練習する

## 実習で使うファイル

- `introductions/自分の名前.md`
- `practice/conflict-message.txt`

`introductions/` フォルダは最初から用意されています。VS Code の Explorer で `introductions` を右クリックして、自分の名前のファイルを作ってください。

## 教材の分け方

この教材では、内容を混ぜずに次の3つに分けています。

- Gitの基本操作: ブランチ作成、commit、push、Pull Request、コンフリクト解消
- レポジトリ内の基本構成: `backend`、`frontend`、`docs`、ルートの `README.md` などに何が入るか
- セキュリティ観点: Git操作で何をしてはいけないか、なぜ危険なのか

振り返るときは、知りたい内容に合わせて該当する資料を見てください。

## 個人作業の基本ルール

実習中の個人作業では、`main` に直接pushしません。

`main` はチーム全員が基準にするブランチです。通常は自分の作業ブランチにpushしてからPull Requestを作り、レビュー後に `main` へ取り込みます。

VS Code 左下のブランチ名が `main` のときは、自分だけの判断でpushしないでください。

## 基本の流れ

```bash
git checkout main
git pull origin main
git checkout -b 作業ブランチ名

# ファイルを編集

git status
git add 対象ファイル
git commit -m "変更内容がわかるメッセージ"
git push origin 作業ブランチ名
```

VS Codeで操作する場合は、左側の Source Control で変更ファイルを確認し、必要なファイルだけ `+` を押してステージングします。

## 危険度の高い操作は自分だけで進めない

チーム開発では、他の人の作業や `main` ブランチに影響する操作があります。

次の操作は、リーダーや講師の指示がある時だけ行います。

- `main` へのpush
- `git push --force`
- `git reset --hard`
- VS Code の `Discard Changes`
- 共有済みブランチでの rebase
- push後の `commit --amend`
- リモートブランチの削除

迷ったら、作業を消さずにVS Codeの画面を見せて相談してください。

## 詳しい手順

- 実習の進め方: [docs/workshop.md](docs/workshop.md)
- VS Codeでの操作: [docs/vscode-guide.md](docs/vscode-guide.md)
- レポジトリ内の基本構成: [docs/repository-structure.md](docs/repository-structure.md)
- セキュリティ観点のGit注意点: [docs/security-git.md](docs/security-git.md)
- 困ったとき: [docs/troubleshooting.md](docs/troubleshooting.md)
