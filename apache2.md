0. sudo apt install apache2
0. cd /var/www/html
0. sudo vi .htaccess
```.htaccess
AuthType Basic # 認証方式の指定
AuthName "Please enter your ID and PW"
AuthUserFile /var/www/html/.htpasswd  #参照するパスワードファイルのパス 
Require valid-user
```
0. cd /etc/apache2
0. sudo vi apache2.conf
```apache2.conf
# 途中省略
<Directory />
	Options FollowSymLinks
	AllowOverride None
	Require all denied
</Directory>

<Directory /usr/share>
	AllowOverride None
	Require all granted
</Directory>

<Directory /var/www/>
	Options Indexes FollowSymLinks
	AllowOverride None
	Require all granted
</Directory>

<Directory /var/www/html> # /var/www/html下の.htaccessファイ ルの設定を読み込む記述を追加
	AllowOverride AuthConfig
</Directory>
```
0. sudo touch .htpasswd
0. sudo htpasswd -c .htpasswd user1 # ユーザー[user1]とパスワードを設定する
0. sudo systemctl restart apache2

ブラウザからサーバが立ち上がっている確認する
http://[ip-adrress]
