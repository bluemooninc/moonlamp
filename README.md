# moonlamp
Docker files for lamp on Vagrant ( nginx, PHP, MySQL )

Vagrant のインストールが済んでいる環境で Docker を Build します。
/vagrant/docker/moonlamp というフォルダにこのリポジトリのファイルを配置します。
/vagrant/html が web root になります。

## 1:Dockerfileのbuild

sudo docker build -t="bluemoon/lamp" .

## 1:Dockerfileの実行

-p ローカルポート:docker 側ポートで 192.168.33.10 にアクセスします。ローカルポートを-p 8080:80 に変更すれば、ブラウザから 192.168.33.10:8080 でアクセスできます。

docker run -i -t -d -p 80:80 -p 22:22 -p 3306:3306 --name moonlamp -v /vagrant:/vagrant:rw bluemoon/lamp

## 第３章　ローカルからアクセス

### 1:ブラウザから
http://192.168.33.10

phpMyAdmin や WordPress などは /vagrant/html/ フォルダにローカルで配置します。
以下にアクセスすると動作します。

http://192.168.33.10/phpMyAdmin
http://192.168.33.10/wordpress

### 2:ターミナルから
ssh -p 22 docker@192.168.33.10
PW は docker

### 3:MySQL Workbench / Aquafold 等から
192.168.33.10:3306 root
pw は root
