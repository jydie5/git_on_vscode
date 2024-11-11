# git コマンドを使わずにvscodeでプルリクエストまで

gitのフローをVSCODEのみで一回り巡回できるようにするドキュメントです。

```bash
# gitの管理下であることを宣言
git init 

# 更新したファイルをステージングエリアに乗せる
git add

# ステージングエリアのファイルをコミットする
git commit -m "コメント"

# リモートにプッシュする
git push -u origin main




```


### git init

![alt text](image.png)

'リポジトリを初期化する'をクリックで終了。

---

### git add .


![alt text](image-1.png)

ここのプラスのボタンを押すと変更があったファイルがステージングエリアに登録されます。

---

### git commit -m (コミットメッセージ)

![alt text](image-2.png)

---

### git push -u origin main

