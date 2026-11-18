# 懸賞応募一覧

応募した懸賞と当選結果を一覧で見られる静的ページです。個人情報（氏名・住所・電話番号・メール・会員ID）は含みません。

- 公開ページ: https://mayuch2525-coder.github.io/kensho-list/
- リポジトリ: https://github.com/mayuch2525-coder/kensho-list

データは `data/entries.csv` です。ページはビルドせず、このファイルを読み込んで表示します。

## 更新方法

### 1. ボックス上のスクリプト（推奨）

サイトの日次ログ（`/workspace/kensho/fruitmail_log.csv` と `dreammail_log.csv`）から一覧を再生成し、コミットして推します。すでに一覧にある「当選結果」と「抽選日/発表日」は、ログに無くてもそのまま残します。

```bash
# ログを反映して推す
python3 /workspace/kensho/update_list.py

# 推さずに確認だけ
python3 /workspace/kensho/update_list.py --no-push

# 当選結果を記録する（同じ日・同じサイトが1件のとき）
python3 /workspace/kensho/update_list.py --result 2026-11-18 ドリームメール 当選

# 抽選日・発表日を記録する
python3 /workspace/kensho/update_list.py --draw-date 2026-11-18 ドリームメール 2026-11-24
```

当選結果は `未発表` / `当選` / `落選` のいずれかです。dry-run とスキップの行は取り込みません。

### 2. GitHub 上で CSV を直接編集する

1. [data/entries.csv](https://github.com/mayuch2525-coder/kensho-list/blob/main/data/entries.csv) を開く
2. 鉛筆アイコンから編集する（「当選結果」や「抽選日/発表日」など）
3. コミットする

ページは数分以内に更新されます。あとからスクリプトを走らせても、手動で直した当選結果と抽選日はそのまま残ります。
