# Node-RED 実習手順

## 目次

### 環境構築

####サーバの構築
  1. VMを作成する
  1. セキュリティ設定する
  1. サーバにSSH接続する

#### アプリケーションのインストール
  1. node.jsとnpmのインストール
  1. Node-REDのインストール
  1. Node-REDの起動

### 操作手順

#### Node-REDの設定
  1. Node-REDへのアクセス
  1. Hello World
  1. twitter情報の取得
  1. センサーデータの情報取得
  1. MQTTで天気情報を取得、メールかtwitterで通知
  1. データの保管

### 環境削除、停止
  1. サーバの停止
  1. サーバの削除
  
  

## 環境構築

### 1. VMを作成する
  作成VMは以下の通り  
  :warning: 途中でDownloadした秘密鍵をかならず保管しておいてください。  

    *light.S1  
    *Ubuntsu Server 14.04 LTS 64-bit  
    *ホスト名：node-red  
    *グループ名：任意  
      
  :information_source:  IDCFコントロール・パネル操作方法の詳細は、[こちら](http://www.idcf.jp/help/cloud/guide/vm_create.html)を参照  

### 2. サーバにセキュリティ設定をする
  ファイアウォール  
    nodered MyIP Custom TCP 1880  
    SSH MyIP SSH 22  

  ポートフォワード  
    ssh TCP 22 TCP 22 node-red  
    nodered HTTP 80 TCP 1880 node-red  

 :information_source:  IDCFコントロール・パネル操作方法の詳細は、[こちら](http://www.idcf.jp/help/cloud/guide/nw_portforward.html)を参照  

### 3. 仮想マシンにSSH接続する
  
* #### Windowsの場合（Tera term使用時）
  
  1. Tera termのDownload  [リンクはこちら](http://osdn.jp/projects/ttssh2/downloads/64118/teraterm-4.89.exe/)から  
  2. exeファイルの実行（Tera termのインストール）
  3. Tera termを起動する  
  4. ホストに実行マシンのIPアドレスを入力  
  5. ユーザー名は「root」、秘密鍵にはVM作成時に使った秘密鍵を指定  
  
  :information_source: 上記説明でよくわからない方は、[こちら](http://www.idcf.jp/help/cloud/guide/pdf/IDCFCloud_installation_guide.pdf)の
P9を参考にしてください。  


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


### 4．仮想マシンにソフトウェアをインストール  

#### Node.jsとnpmのインストール  

  ```sh
sudo add-apt-repository ppa:chris-lea/node.js 
sudo apt-get update
sudo apt-get install nodejs
sudo apt-get install npm
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

### 5. Node-REDの設定  
#### Node-REDへのアクセス  
  
ブラウザより以下にアクセスする。XXXはnode-REDの起動しているサーバのグローバルIPアドレスを入力する。  
http://XXX.XXX.XXX.XXX:1880  
  
  
    
## Node-RED操作手順  
  
#### Hello World  
#### twitter情報の取得  
#### センサーデータの情報取得  
#### MQTTで天気情報を取得  
#### データの保管  

:information_source: こちらのサイトに詳しい情報があります。興味がでてきたらこちらで調べてみてください。[http://nodered.org/docs/](http://nodered.org/docs/)  
  
  
  
## 環境の停止、削除 
  

#### サーバの停止、削除  
1. IDCFクラウドコンソールから、西日本リージョン > コンピューティングを選択。  
2. 仮想マシンを選択。  
3. 該当サーバの停止、削除を行います。  
  
*停止ではDiskの課金はとまりません。完全に課金を止めたい場合は削除してください。 


 
 
 



