# 実習手順

このページでは、実際に手を動かしてGitの基本操作を練習します。

## 事前準備

GitHub上でこのレポジトリを自分のPCにcloneしてください。

```bash
git clone リポジトリURL
cd git-practice
```

## 実習1: 作業ブランチを作る

まず `main` に移動します。

```bash
git checkout main
```

リモートの最新状態を取り込みます。

```bash
git pull origin main
```

自分の作業ブランチを作ります。

```bash
git checkout -b 自分の名前_dev
```

例:

```bash
git checkout -b sho_dev
```

## 実習2: 自己紹介ファイルを追加する

`introductions/` の中に、自分の名前のMarkdownファイルを作ります。

例:

```text
introductions/sho.md
```

内容は次のように書いてください。

```markdown
# sho

- 好きなこと:
- 触ってみたい技術:
- 一言:
```

## 実習3: 画面ファイルを編集する

`app/views/users/index.html.erb` を開き、自分の名前を1行追加してください。

例:

```erb
<li>sho</li>
```

## 実習4: 変更を確認する

```bash
git status
```

どのファイルが変更されたかを確認します。

## 実習5: ステージングする

```bash
git add introductions/sho.md
git add app/views/users/index.html.erb
```

まとめてステージングする場合は次のコマンドでも大丈夫です。

```bash
git add .
```

## 実習6: コミットする

```bash
git commit -m "add sho introduction"
```

コミットメッセージは、何を変更したかわかる内容にします。

よい例:

```bash
git commit -m "add sho introduction"
git commit -m "update user list"
```

避けたい例:

```bash
git commit -m "fix"
git commit -m "aaa"
```

## 実習7: pushする

```bash
git push origin 自分の名前_dev
```

例:

```bash
git push origin sho_dev
```

`main` にpushしてはいけません。

```bash
git push origin main
```

## 実習8: Pull Requestを作る

GitHubでPull Requestを作成します。

- base: `main`
- compare: 自分の作業ブランチ

Pull Requestには、何を変更したかを書いてください。

例:

```markdown
## やったこと

- 自己紹介ファイルを追加しました
- ユーザー一覧に名前を追加しました
```

## コンフリクト練習

複数人が同じ行を編集すると、コンフリクトが起きることがあります。

コンフリクトが起きたら、次の流れで解消します。

```bash
git checkout コンフリクトしたブランチ名
git checkout main
git pull origin main
git checkout コンフリクトしたブランチ名
git merge main
```

コンフリクトしたファイルを開き、残したい内容を選びます。

修正できたら次のコマンドを実行します。

```bash
git add .
git commit -m "modify conflict"
git push origin コンフリクトしたブランチ名
```

Pull Request画面で `Conflicting files` が消えたら完了です。

