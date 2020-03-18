# learning-python



Java, C# のエンジニアがPythonを学習します。
Pythonに関する知識は、現在下記です。

1. 動的型紐付けの言語である
1. 分析を行う関数が豊富にある
1. 関数型の処理が使える？？
1. MyPyを使うことで、静的型紐付けの言語のように開発できる
1. IDEはPyCharmがいいらしい
1. pipenvなど仮想化？コンテナ化？の仕組みがある
1. テストフレームワークがしっかりしてそう
1. パッケージ名をシンプルにつける

不安な点は、動的型紐付けである点が何より不安です。



## 開発環境構築



トライアンドエラーで開発していくことになると思うので、Dockerで開発環境つくります。
Virtualbox上のLinuxMintに、Dockerで完全なLinuxMint艦橋作って、そのコンテナにリモートデスクトップ接続して開発します。（Windows 10 Pro買ったと思ってたのに、Homeだった・・・）

下記の手順で作成します

1. 仮想マシン上にLinuxMintをインストール
2. インストールディスクのCDから再度起動し、1でインストールされた/以下すべてtarで固める
3. 今度はハードディスクから起動し、docker.ioをaptでインストール
4. scratchをベースにtarしたファイルをコンテナの/に展開してdockerイメージを作成（mint-base:19.3とする）
5. mint-baseのコンテナのを元にxrdpなどをインストールしたdockerイメージを作成（mint-xrdp:19.3とする）
   （[yama07/docker-ubuntu-lxde](https://hub.docker.com/r/yama07/docker-ubuntu-lxde/) と [
   LinuxMint 19: Cinnamonデスクトップ環境にXRDPで接続する](https://www.hiroom2.com/2018/07/11/linuxmint-19-xrdp-cinnamon-ja/)を参考にした。ただし、未だリモートデスクトップ接続時に音ならせず）
6. mint-xrdpをベースにgit・openjdl-11-jdkをaptインストール、pycharmをcurlでダウンロードして、/etc/skel に展開したdockerイメージを作成（mint-pycharm:19.3とする）
7. mint-pycharm:19.3 にapt upgradeしたdockerイメージを作成（mint-pycharm:latestとする）



## とりあえず動かしてみる



作成したイメージを元にコンテナを立ち上げ、PyCharmで新規のプロジェクトを作成し、下記コードでモジュールを作成

動かしてみる

```python
print('aaa')
```



作成したコードを右クリックからRUNするとコンソールメニューにaaaと表示され、とりあえず動くことを確認



課題：

- pythonのバージョンが3.6 古くない？：2020.03.19時点。最新は3.8.2？
  ●プロジェクトの設定のpythonのバージョン確認方法
  メニューのFile->Settings->project interpreter
  ※プロジェクト右クリックでは設定できないので注意
- venvじゃなくてpipenvのほうがいいんじゃないっけ？
  ->ググってみた。よくわからないが、pipenvのが良さそう
- pycharmの初期設定がめんどくさい
  ->初期設定した状態のイメージを作る・・・か？









