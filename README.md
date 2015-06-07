# moonlamp
Docker files for lamp on Vagrant ( nginx, PHP, MySQL )

Vagrant のインストールが済んでいる環境で Docker を Build します。
/vagrant/docker/moonlamp というフォルダにこのリポジトリのファイルを配置します。
/vagrant/html が web root になります。

## 第１章 Dockerfileのbuild

sudo docker build -t="bluemoon/moonlamp" .

## 第２章 Dockerfileの実行

-p ローカルポート:docker 側ポートで 192.168.33.10 にアクセスします。ssh -p 2222 docker@192.168.33.10 で docker に ssh できます。vagrant は vagrant ssh で 22 で接続するので、docker では 22 ポートは使えません。

docker run -i -t -d -p 80:80 -p 2222:22 -p 3306:3306 --name moonlamp -v /vagrant:/vagrant:rw bluemoon/moonlamp

## 第３章　ローカルからアクセス

### 1:ブラウザから
http://192.168.33.10

phpMyAdmin や WordPress などは /vagrant/html/ フォルダにローカルで配置します。
例えば wordpress のサイトならサーバ上のファイルを /vagrant/html/  直下に置くと動作します。

### 2:ターミナルから
ssh -p 2222 docker@192.168.33.10
PW は docker

### 3:MySQL Workbench / Aquafold 等から
192.168.33.10:3306 root
pw は root
