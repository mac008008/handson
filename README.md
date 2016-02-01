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


mqtt-broker node
　Server 210.140.70.34
　Port 1883

天気情報
 UUID(Client ID) : d39eba6f-29a4-440b-83e2-728b55749f68
 Username: d39eba6f-29a4-440b-83e2-728b55749f68
 Token(Password): 8dc1bffc

センサー情報 
 UUID(Client ID) : 3ae70879-83e2-49c8-9b6d-320f99bed601
 Username: 3ae70879-83e2-49c8-9b6d-320f99bed601
 Token(Password): 096709d8
 
 
 [{"id":"a7d4c441.582b38","type":"mqtt-broker","z":"c7365413.38c9a8","broker":"210.140.70.34","port":"1883","clientid":"3ae70879-83e2-49c8-9b6d-320f99bed601","usetls":false,"verifyservercert":true,"compatmode":true,"keepalive":"15","cleansession":true,"willTopic":"","willQos":"0","willRetain":null,"willPayload":"","birthTopic":"","birthQos":"0","birthRetain":null,"birthPayload":""},{"id":"f170f5c3.0e8f08","type":"mqtt-broker","z":"c7365413.38c9a8","broker":"210.140.70.34","port":"1883","clientid":"d39eba6f-29a4-440b-83e2-728b55749f68","usetls":false,"verifyservercert":true,"compatmode":true,"keepalive":"15","cleansession":true,"willTopic":"","willQos":"0","willRetain":null,"willPayload":"","birthTopic":"","birthQos":"0","birthRetain":null,"birthPayload":""},{"id":"97cb50a9.6834b","type":"mqtt in","z":"c7365413.38c9a8","name":"action-4","topic":"d39eba6f-29a4-440b-83e2-728b55749f68","broker":"f170f5c3.0e8f08","x":101.5,"y":393,"wires":[["26b9650c.d9469a"]]},{"id":"26b9650c.d9469a","type":"json","z":"c7365413.38c9a8","name":"parse","x":282.5,"y":395,"wires":[["cf3415c0.30cbe8","c79d6301.3862a"]]},{"id":"cf3415c0.30cbe8","type":"switch","z":"c7365413.38c9a8","name":"check_weather","property":"payload","propertyType":"msg","rules":[{"t":"regex","v":"雨","vt":"str","case":false},{"t":"else"}],"checkall":"true","outputs":2,"x":242.5,"y":556,"wires":[["a262d14c.5d9d3"],["54ad7856.ab5288"]]},{"id":"a262d14c.5d9d3","type":"e-mail","z":"c7365413.38c9a8","server":"smtp.gmail.com","port":"465","name":"mac008008@gmail.com","dname":"雨　イベント中止の連絡","x":561.5,"y":428,"wires":[]},{"id":"5d5195d6.a2ae6c","type":"comment","z":"c7365413.38c9a8","name":"天気情報","info":"","x":82.5,"y":349,"wires":[]},{"id":"62cca0b4.9d336","type":"comment","z":"c7365413.38c9a8","name":"温度センサー","info":"","x":99.5,"y":732,"wires":[]},{"id":"c79d6301.3862a","type":"debug","z":"c7365413.38c9a8","name":"記録","active":false,"console":"false","complete":"payload","x":450.5,"y":366,"wires":[]},{"id":"8cd42643.732bd8","type":"mqtt in","z":"c7365413.38c9a8","name":"action-3","topic":"3ae70879-83e2-49c8-9b6d-320f99bed601","broker":"a7d4c441.582b38","x":100.5,"y":801,"wires":[["6e28d325.91d72c","33c5c2bb.cc3a3e"]]},{"id":"54ad7856.ab5288","type":"e-mail","z":"c7365413.38c9a8","server":"smtp.gmail.com","port":"465","name":"mac008008@gmail.com","dname":"雨以外　イベント開催連絡","x":542.5,"y":581,"wires":[]},{"id":"72c372bc.8d3c8c","type":"function","z":"c7365413.38c9a8","name":"Convert Payload gyro","func":"var gyroX = msg.payload.d.gyroX;\nvar gyroY = msg.payload.d.gyroY;\nvar gyroZ = msg.payload.d.gyroZ;\n\nmsg.payload = {\n    x: gyroX,\n    y: gyroY,\n    z: gyroZ\n};\n\nreturn msg;","outputs":1,"noerr":0,"x":399.5,"y":670,"wires":[[]]},{"id":"73908249.8c6f7c","type":"switch","z":"c7365413.38c9a8","name":"","property":"payload.data.payload.objctTemperature","propertyType":"msg","rules":[{"t":"gte","v":"25","vt":"num"},{"t":"else"}],"checkall":"true","outputs":2,"x":360.5,"y":717,"wires":[["aa5b11e.f55a4f","b84a2823.47b5d8"],["121f2197.ede0de"]]},{"id":"121f2197.ede0de","type":"debug","z":"c7365413.38c9a8","name":"異常なし","active":true,"console":"false","complete":"payload","x":560.5,"y":779,"wires":[]},{"id":"6e28d325.91d72c","type":"json","z":"c7365413.38c9a8","name":"parse2","x":164.5,"y":884,"wires":[["73908249.8c6f7c"]]},{"id":"aa5b11e.f55a4f","type":"debug","z":"c7365413.38c9a8","name":"温度異常","active":true,"console":"false","complete":"payload","x":526.5,"y":711,"wires":[]},{"id":"33c5c2bb.cc3a3e","type":"debug","z":"c7365413.38c9a8","name":"","active":false,"console":"false","complete":"true","x":344.5,"y":842,"wires":[]},{"id":"b84a2823.47b5d8","type":"e-mail","z":"c7365413.38c9a8","server":"smtp.gmail.com","port":"465","name":"mac008008@gmail.com","dname":"異常メール","x":677.5,"y":659,"wires":[]}]
 
 
 



