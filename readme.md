# git コマンドを使わずにvscodeでプルリクエストまで

gitのフローをVSCODEのみで以下のコマンドを打たず、一回り巡回できるようにするドキュメントです。

```bash
# gitの管理下であることを宣言
git init 

# 更新したファイルをステージングエリアに乗せる
git add

# ステージングエリアのファイルをコミットする
git commit -m "コメント"

# リモートにプッシュする
git push -u origin main

#新しいブランチを作成
git checkout -b 新しいブランチ
git switch -c 新しいブランチ

#ブランチの移動
git checkout ブランチ名
git switch ブランチ名

# マージ
重要）「指定したブランチにあるコミット」を「今のブランチ」に反映させる
git merge 指定ブランチ名　# （つまり今はmasterにいる）
git merge feature

#　前の状態に戻す
git restore . --source 戻したい場所　#指定位置まで戻す
今いる場所が「HEAD」です
git restore . --source HEAD~1   #（一個前のコミットに戻す）
git restore . --source HEAD~2   #（2個前のコミットに戻す）

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

コミットメッセージを入力してコミットを押す。

---

### githubにリモートリポジトリを作成する

![alt text](image-3.png)

Branchの発行でリポジトリがgithub上に作成されます


![alt text](image-4.png)

プライベートとパブリックの選択

![alt text](image-5.png)

githubにコードがpushされました。




---
### git push -u origin main

上記の流れをコミットの単位で巡回していきます。

ファイル更新＞ステージング＞コミット＞リモートにプッシュ

![alt text](image-6.png)

以後はコミットが終わると、リモートにプッシュするボタンが出ます。

---

### git checkout -b 新しいブランチ
### git switch -c 新しいブランチ

![alt text](image-7.png)

vscode左下のこのボタンを押す。

![alt text](image-8.png)

新しいブランチに名前をつけて作成。

![alt text](image-9.png)

futureというブランチが作成され移動もしました。

![alt text](image-11.png)

以降はmainとfutureを移動できるようになります。
それぞれでcommitなどは別に管理されます。
futureでもリモートブランチを作成しておきます。


---

### プルリクエスト（分岐したブランチをmain,masterにマージする）

vscodeの拡張機能でgithub pull requestsをインストールする

![alt text](image-12.png)

![alt text](image-13.png)

上記拡張機能を入れるとこの場所にプルリクエストボタンが出ます。

![alt text](image-14.png)

プルリクエスト作成画面になります。

![alt text](image-15.png)

merge pull requestを押す


![alt text](image-16.png)

create merge commitを押す

![alt text](image-17.png)

コミット完成しました。ここでfutureブランチを消すこともできます。

---

### mainブランチに戻り、マージした差分をローカルにプルする

マージが終わるとvscodeのブランチの横に、マージされた差分の数が出ます。

これをリモートからプルして、一周完了です。

![alt text](image-18.png)







---

### ブランチの削除
・安全に削除
```bash
	git branch -d <ブランチ名>　　（マージされている場合はこれで通る）
	git branch -D <ブランチ名>	（マージされていないブランチを強制削除）
```

・　削除時の注意点
#現在チェックアウトされているブランチは削除できない: 削除しようとしているブランチが現在の作業ブランチ（HEADが指しているブランチ）である場合、Gitは削除を拒否します。別のブランチに切り替えてから削除する必要があります。
```bash
例）git switch main
	git branch -d feature-branch
```