# 実習進行表

参加者全員を同じチームのメンバーに見立てて進めます。

## 前半: 正しい作業フローを練習する

各自が自分専用の自己紹介ファイルを追加します。別々のファイルを編集するので、基本的にコンフリクトは起きません。

### Step 1: cloneする

```bash
git clone https://github.com/watnow2026/git-practice.git
cd git-practice
```

すでにclone済みの場合は、cloneし直さずにそのフォルダへ移動してください。

```bash
cd git-practice
```

### Step 2: mainに移動する

```bash
git checkout main
```

### Step 3: mainを最新にする

```bash
git pull origin main
```

### Step 4: 自分の作業ブランチを作る

```bash
git checkout -b 自分の名前_dev
```

例:

```bash
git checkout -b sho_dev
```

### Step 5: 自己紹介ファイルを追加する

`introductions/` の中に、自分の名前のファイルを作ります。

例:

```text
introductions/sho.md
```

内容:

```markdown
# sho

- 好きなこと:
- 触ってみたい技術:
- 一言:
```

### Step 6: 変更状況を確認する

```bash
git status
```

自分が追加したファイルが表示されていることを確認します。

### Step 7: ステージングする

```bash
git add introductions/自分の名前.md
```

例:

```bash
git add introductions/sho.md
```

### Step 8: コミットする

```bash
git commit -m "add 自分の名前 introduction"
```

例:

```bash
git commit -m "add sho introduction"
```

### Step 9: 自分のブランチにpushする

```bash
git push origin 自分の名前_dev
```

例:

```bash
git push origin sho_dev
```

`main` にはpushしません。

```bash
git push origin main
```

### Step 10: Pull Requestを作る

GitHubでPull Requestを作ります。

- base: `main`
- compare: 自分の作業ブランチ

Pull Requestには、変更内容を書きます。

```markdown
## やったこと

- 自己紹介ファイルを追加しました
```

Pull Requestを作ったら、講師または先輩にレビューしてもらいます。レビュー後、問題なければmergeしてもらいます。

## 後半: コンフリクト解消を練習する

全員または数名で、同じファイルの同じ行を編集します。

使うファイル:

```text
practice/conflict-message.txt
```

### Step 1: mainを最新にする

```bash
git checkout main
git pull origin main
```

### Step 2: コンフリクト練習用ブランチを作る

```bash
git checkout -b 自分の名前_conflict
```

例:

```bash
git checkout -b sho_conflict
```

### Step 3: 同じ行を書き換える

`practice/conflict-message.txt` の1行目を、自分の好きな内容に書き換えます。

### Step 4: commitしてpushする

```bash
git status
git add practice/conflict-message.txt
git commit -m "update conflict message"
git push origin 自分の名前_conflict
```

### Step 5: Pull Requestを作る

GitHubでPull Requestを作ります。

先に1人のPull Requestをmergeします。残りの人のPull Requestでは、コンフリクトが起きます。

### Step 6: コンフリクトしたブランチでmainを取り込む

```bash
git checkout 自分の名前_conflict
git checkout main
git pull origin main
git checkout 自分の名前_conflict
git merge main
```

### Step 7: コンフリクト箇所を修正する

ファイルを開くと、次のような表示があります。

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

### Step 8: 解消内容をcommitしてpushする

```bash
git add .
git commit -m "modify conflict"
git push origin 自分の名前_conflict
```

GitHubのPull Request画面で `Conflicting files` が消えていれば完了です。

## 講師・先輩がやること

- 参加者をGitHubリポジトリのメンバーに追加する
- `main` への直接pushは禁止だと最初に伝える
- 前半のPull Requestはレビューしてからmergeする
- 後半は先に1人のPull Requestだけmergeして、残りの人にコンフリクトを体験してもらう

