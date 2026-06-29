# 実習進行表

参加者全員を同じチームのメンバーに見立てて進めます。

コマンドを打つ前に、VS Code 左下のブランチ名を毎回確認してください。

## 前半: 正しい作業フローを練習する

各自が自分専用の自己紹介ファイルを追加します。別々のファイルを編集するので、基本的にコンフリクトは起きません。

### Step 1: cloneする

```bash
git clone https://github.com/watnow2026/git-practice.git
cd git-practice
```

VS Codeで `git-practice` フォルダを開きます。

すでにclone済みの場合は、cloneし直さずにそのフォルダをVS Codeで開いてください。

### Step 2: mainに移動する

VS Code左下のブランチ名を確認します。

`main` ではない場合は、左下のブランチ名をクリックして `main` を選びます。

ターミナルで行う場合:

```bash
git checkout main
```

### Step 3: mainを最新にする

VS Code の Source Control で `Sync Changes` または更新ボタンを使います。

ターミナルで行う場合:

```bash
git pull origin main
```

成功した状態:

- VS Code左下のブランチ名が `main`
- Source Control に不要な変更が残っていない

### Step 4: 自分の作業ブランチを作る

VS Code左下の `main` をクリックし、`Create new branch` を選びます。

ブランチ名は次の形にします。

```text
自分の名前_dev
```

例:

```text
sho_dev
```

ターミナルで行う場合:

```bash
git checkout -b sho_dev
```

成功した状態:

- VS Code左下のブランチ名が自分の作業ブランチになっている

### Step 5: 自己紹介ファイルを追加する

VS Code の Explorer で `introductions` フォルダを右クリックし、`New File` を選びます。

ファイル名は英数字で作ります。

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

成功した状態:

- `introductions/自分の名前.md` が作成されている
- ファイルが保存されている

### Step 6: 変更状況を確認する

VS Code左側の Source Control アイコンを開きます。

自分が追加したファイルだけが表示されていることを確認します。

ターミナルで行う場合:

```bash
git status
```

### Step 7: ステージングする

Source Control の変更ファイル一覧で、追加した自己紹介ファイルの `+` を押します。

ターミナルで行う場合:

```bash
git add introductions/sho.md
```

`git add .` は便利ですが、関係ないファイルまで含めることがあります。実習では対象ファイルを確認してからステージングします。

### Step 8: コミットする

Source Control のメッセージ欄に、変更内容がわかるメッセージを書きます。

例:

```text
add sho introduction
```

`Commit` ボタンを押します。

ターミナルで行う場合:

```bash
git commit -m "add sho introduction"
```

成功した状態:

- Source Control に未コミットの変更が残っていない

### Step 9: 自分のブランチにpushする

VS Code の `Publish Branch` を押します。

ターミナルで行う場合:

```bash
git push origin sho_dev
```

push前の確認:

- VS Code左下のブランチ名が自分の作業ブランチになっている
- `main` ではない
- Source Control に未コミットの変更が残っていない

### Step 10: Pull Requestを作る

GitHub のリポジトリページを開きます。

1. `Compare & pull request` を押す
2. base が `main` になっていることを確認する
3. compare が自分の作業ブランチになっていることを確認する
4. タイトルを書く
5. 本文に「やったこと」を書く
6. `Create pull request` を押す
7. Pull RequestのURLを講師または先輩に共有する

本文の例:

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

VS Code左下のブランチ名を `main` に切り替え、最新状態にします。

ターミナルで行う場合:

```bash
git checkout main
git pull origin main
```

### Step 2: コンフリクト練習用ブランチを作る

VS Code左下の `main` をクリックし、`Create new branch` を選びます。

ブランチ名:

```text
自分の名前_conflict
```

例:

```text
sho_conflict
```

ターミナルで行う場合:

```bash
git checkout -b sho_conflict
```

### Step 3: 同じ行を書き換える

`practice/conflict-message.txt` の1行目を、自分の好きな内容に書き換えます。

### Step 4: commitしてpushする

Source Control で変更ファイルを確認し、`practice/conflict-message.txt` だけをステージングします。

コミットメッセージ:

```text
update conflict message
```

ターミナルで行う場合:

```bash
git status
git add practice/conflict-message.txt
git commit -m "update conflict message"
git push origin sho_conflict
```

### Step 5: Pull Requestを作る

GitHubでPull Requestを作ります。

先に1人のPull Requestをmergeします。残りの人のPull Requestでは、コンフリクトが起きます。

### Step 6: コンフリクトしたブランチでmainを取り込む

VS Code左下のブランチ名が自分のコンフリクト練習用ブランチになっていることを確認します。

ターミナルで行う場合:

```bash
git checkout sho_conflict
git checkout main
git pull origin main
git checkout sho_conflict
git merge main
```

### Step 7: VS Codeでコンフリクト箇所を修正する

コンフリクトしたファイルを開くと、VS Codeに次のボタンが表示されます。

- `Accept Current Change`: 今いる自分のブランチ側の変更を残す
- `Accept Incoming Change`: 取り込もうとしている `main` 側の変更を残す
- `Accept Both Changes`: 両方の変更を残す
- `Compare Changes`: 差分を見比べる

残したい内容を選びます。必要なら手で文章を編集しても大丈夫です。

修正後、`<<<<<<<`、`=======`、`>>>>>>>` の記号がファイル内に残っていないことを確認します。

### Step 8: 解消内容をcommitしてpushする

Source Control でコンフリクトを解消したファイルをステージングし、commitしてpushします。

ターミナルで行う場合:

```bash
git add practice/conflict-message.txt
git commit -m "modify conflict"
git push origin sho_conflict
```

GitHubのPull Request画面で `Conflicting files` が消えていれば完了です。

## 講師・先輩がやること

- 参加者をGitHubリポジトリのメンバーに追加する
- 必要に応じて branch protection rule を設定する
- 最初にVS Code左下のブランチ名を見ることを画面共有で説明する
- 実習中は「今どのブランチにいるか」を何度も確認させる
- 前半のPull Requestはレビューしてからmergeする
- 後半は先に1人のPull Requestだけmergeして、残りの人にコンフリクトを体験してもらう
- 危険操作が必要な場合は、誰が、なぜ、いつ行うかを明示する
