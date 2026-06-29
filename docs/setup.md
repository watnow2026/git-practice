# 事前準備

実習を始める前に、次を確認してください。

## 必要なもの

- VS Codeをインストールしている
- Gitをインストールしている
- GitHubアカウントにログインできる
- このリポジトリにアクセスできる
- GitHubへpushできる認証状態になっている
- Gitの `user.name` と `user.email` が設定されている

## 確認コマンド

VS Codeの統合ターミナル、または普段使っているターミナルで確認します。

```bash
git --version
git config user.name
git config user.email
```

名前やメールアドレスが表示されない場合は、講師または先輩に相談してください。

## GitHubの確認

次を確認してください。

- GitHubにログインできる
- `watnow2026/git-practice` を開ける
- リポジトリの画面が見える
- 自分のブランチをpushできる権限がある

pushでログインを求められた場合は、自分だけで進めずに講師または先輩に画面を見せてください。

## ブランチ名のルール

実習では、ブランチ名にGitHub IDを使います。

例:

```text
github-id_dev
github-id_conflict
```

実際の例:

```text
sho_dev
sho_conflict
```

ルール:

- 英小文字、数字、ハイフン、アンダースコアだけを使う
- 空白を入れない
- 日本語を使わない
- 他の参加者と重ならない名前にする
