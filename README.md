# Node-RED 実習手順

## 目次

### サーバの構築
  1. VMを作成する
  1. セキュリティ設定する
  1. サーバにSSH接続する

### アプリケーションのインストール
  1. node.jsとnpmのインストール
  1. Node-REDのインストール
  1. Node-REDの起動

### Node-REDの設定
  1. Node-REDへのアクセス
  1. Hello World
  1. twitter情報の取得
  1. センサーデータの情報取得
  1. データの保管

### 1. VMを作成する
*作成VMは以下の通り
  *light.S1
  *Ubuntsu Server 14.04 LTS 64-bit
  *ホスト名：node-red
  *グループ名：任意
:warning: IDCFコントロール・パネル操作方法の詳細は、http://www.idcf.jp/help/cloud/guide/vm_create.htmlを参照

### 2. サーバにセキュリティ設定をする
ファイアウォール
nodered MyIP Custom TCP 1880
mqtt 0.0.0.0/0 Custom 1883 
SSH MyIP SSH 22 

ポートフォワード
ssh TCP 22 TCP 22 node-red
nodered TCP 1880 TCP 1880 node-red
mqtt TCP 1883 TCP 1883 node-red

:warning: IDCFコントロール・パネル操作方法の詳細は、http://www.idcf.jp/help/cloud/guide/nw_portforward.htmlを参照

### 3. 仮想マシンにSSH接続する

* #### Windowsの場合（Tera term使用時）

  1. Tera termを起動する
  2. ホストに実行マシンのIPアドレスを入力
  3. ユーザー名は「root」、秘密鍵にはVM作成時に使った秘密鍵を指定
  
* #### Mac、Linuxの場合

  1. ターミナルを開く
  2. VM作成時に使った秘密鍵のパーミッションを600に変更する

    ```bash
    chmod 600 ssh_private_key
    ```

  3. 仮想マシンにSSH接続する

    ```bash
    ssh root@xxx.xxx.xxx.xxx -i ssh_private_key
    ```


### 3．仮想マシンにソフトウェアをインストール

#### Node.jsとnpmのインストール

  ```sh
sudo add-apt-repository ppa:chris-lea/node.js 
sudo apt-get update
sudo apt-get install nodejs npm
node -v
v0.10.37
  ```

#### node-REDのインストール

  ```sh
  sudo npm install -g --unsafe-perm node-red
  ```
  
node-gypで多少エラーがでますが、動作に影響はないので気にせずにさきにすすみます。
  
#### node-REDの起動

  ```
  node-red
  ```
