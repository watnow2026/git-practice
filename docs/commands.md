# Gitコマンド早見表

## ブランチ移動

```bash
git checkout main
```

## リモートの最新状態を取り込む

```bash
git pull origin main
```

## 作業ブランチを作成して移動する

```bash
git checkout -b 作業ブランチ名
```

例:

```bash
git checkout -b sho_dev
```

## 変更状況を確認する

```bash
git status
```

## ステージングする

```bash
git add ファイル名
```

まとめてステージングする場合:

```bash
git add .
```

## コミットする

```bash
git commit -m "変更内容がわかるメッセージ"
```

## 作業ブランチをpushする

```bash
git push origin 作業ブランチ名
```

## やってはいけない操作

```bash
git push origin main
```

`main` に直接pushすると、レビューなしで大元のソースコードを変更してしまいます。

