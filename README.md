# **git**の使い方

## gitの基本的なコマンド

基本的なgitコマンドの説明を記します。

参考資料

[Gitコマンドチートシート](https://qiita.com/kamihork/items/36992c14c70b7477f40e)
```
git clone ~~
```
レポジトリからローカルにクローンしてきます。

```
git init
```
新規リポジトリの作成が行えます。レポジトリにしたいファイル内にcdで移動し、このコマンドを打ちましょう。

```
git add .
git commit -m "commit"
git push origin master
```
ローカルからgitにpushします。

**注意**

このままコピーしても使えますが、masterにpushする時だけにしてください。
基本的に"commit"の部分はコミットメッセージに、masterの部分はbranch名に変えてください。

```
git pull
```
ローカルにレポジトリのファイルはあるものの、古いバージョンである場合、また、ローカルの情報にbranch名がない場合これを使います。

```
git checkout master
```
ローカルの作業branchを変えます。masterの部分は、変えたいbranch名に変えてください。なお、
```
git checkout -b [branch]
```
で、ローカルでbranch作成とともに、そのbranchに移動できます。

```
git branch
```
現在のbranchを確認できます。全てのbranchを確認したい場合、
```
git branch -a
```
で、確認できます。他にも、branchコマンドは、
```
git branch [branch]
```
で、新規branch作成が出来たり、
```
git branch -d [branch]

```
で、branchを削除が可能です。ただし、カレントbranchはcheckout後でないとdelete出来ません。

```
git merge [branch]
```
カレントbranchに、選択branchを統合します。

```
git status
```
状態の確認が出来ます。

```
git show [id]
```
変更の確認が出来ます。

```
git log
```
ログが確認出来ます。なお、
```
git log [branch]
```
で、指定branchのログを確認出来ます。

```
git config -l 
```
gitの設定を表示出来ます。

```
git cat-file -p [hash]
```
commit情報を確認出来ます。

```
git diff [id1] [id2]
```
差分を確認出来ます。

gitコマンドはここに乗っていること以外にも、基本的になんでも出来ますが、branch作成や削除、mergeはgit hubや、git lab上で行う方が、ミスが少ない、わかりやすい等の利点があるので、これらはUIのあるgit hub、git lab上で行いましょう。

---

## issueの使い方から、branchの作成、mergeまでの手順

基本的に、複数人で作業する場合、masterで作業するのでなく、branchを切って作業し,そのbranchをmasterにmergeしてください。そうでないと、エラーが発生する可能性が高まり、管理が大変になり、混乱がおきます。

なので、いつも行っている方法を記します。

### issueを作成する

* issue
* New issue
* タイトル入力
* Submit issue

### branchを作成する

* issue
* 作成したissue名
* Create merge request and branchのドロップダウンをクリック
* create branch
* branch名を入力
* create branchボタンをクリック

### mergeする

* ローカルで作業する
* issue
* 作成したissue名
* 作業していたbranch名
* create merge request
* Squash commits when merge request is acceptedにチェック
* Submit merge request
* Mergeをクリック

branch作成の際、ラベルを付けたり、Assigneesを設定したりすると尚良い。

mergeした時、コンフリクトが発生する場合がよくある。その場合、ローカルでも直せるが、わかりにくい上に難しい。なので、git lab上で作業することをお勧めする。
