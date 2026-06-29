# 実習進行表

参加者全員を同じチームのメンバーに見立てて進めます。

コマンドを打つ前に、VS Code 左下のブランチ名を毎回確認してください。

実習前に [setup.md](setup.md) で事前準備を確認してください。

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

VS Code の Source Control で `Pull` を使います。

`Sync Changes` は pull だけでなく push も含むことがあります。`main` 上で `Sync Changes` が表示された場合は、押す前に講師または先輩に相談してください。

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
github-id_dev
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

- `introductions/github-id.md` が作成されている
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

PRを作る前に確認します。

- VS Code左下のブランチ名が自分の作業ブランチ
- Source Control に未コミットの変更が残っていない
- GitHubに自分のブランチをpush済み

GitHub のリポジトリページを開きます。

1. `Compare & pull request` を押す
2. base が `main` になっていることを確認する
3. compare が自分の作業ブランチになっていることを確認する
4. タイトルを書く
5. 本文に「やったこと」を書く
6. `Create pull request` を押す
7. Pull RequestのURLを講師または先輩に共有する

`Compare & pull request` が表示されない場合:

1. GitHubのリポジトリページで `Pull requests` タブを開く
2. `New pull request` を押す
3. base に `main` を選ぶ
4. compare に自分の作業ブランチを選ぶ
5. 差分を確認する
6. `Create pull request` を押す

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

このときも `Sync Changes` ではなく、`Pull` を使います。`main` 上で未pushのcommitがあるように見える場合は、自分だけで進めずに相談してください。

ターミナルで行う場合:

```bash
git checkout main
git pull origin main
```

### Step 2: コンフリクト練習用ブランチを作る

VS Code左下の `main` をクリックし、`Create new branch` を選びます。

ブランチ名:

```text
github-id_conflict
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

PRを作る前に、base が `main`、compare が自分のコンフリクト練習用ブランチになっていることを確認します。

先に1人のPull Requestをmergeします。残りの人のPull Requestでは、コンフリクトが起きます。

### Step 6: コンフリクトしたブランチでmainを取り込む

VS Code左下のブランチ名が自分のコンフリクト練習用ブランチになっていることを確認します。

VS Codeで行う場合:

1. 左下のブランチ名をクリックして `main` に切り替える
2. Source Controlで `Pull` を実行し、ローカルの `main` を最新にする
3. 左下のブランチ名をクリックして、自分のコンフリクト練習用ブランチに戻る
4. Command Paletteを開く
5. `Git: Merge Branch...` を選ぶ
6. `main` を選ぶ
7. コンフリクトが表示されたら、次のStepへ進む

ローカルの `main` が最新でないと、先にmergeされた参加者の変更を取り込めず、コンフリクトが再現されないことがあります。VS Codeの表示はバージョンや拡張機能によって変わることがあるため、画面操作で迷う場合は、このStepだけ統合ターミナルを使ってください。

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

VS Codeで行う場合:

1. Source Controlで `practice/conflict-message.txt` を確認する
2. `+` を押してステージングする
3. メッセージ欄に `modify conflict` と入力する
4. `Commit` を押す
5. `Push` または `Sync Changes` を押す前に、左下が自分のコンフリクト練習用ブランチであることを確認する

ターミナルで行う場合:

```bash
git add practice/conflict-message.txt
git commit -m "modify conflict"
git push origin sho_conflict
```

GitHubのPull Request画面で `Conflicting files` が消えていれば完了です。

## 講師・先輩向け

実習前の権限確認、branch protection、事故対応、コンフリクト練習の進行方法は [instructor-guide.md](instructor-guide.md) を見てください。
