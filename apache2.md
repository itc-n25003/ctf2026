1. sudo apt install apache2
2. cd /var/www/html
3. sudo vi .htaccess
```
# .htaccessの設定
AuthType Basic # 認証方式の指定
AuthName "Please enter your ID and PW"
AuthUserFile /etc/apache2/.htpasswd  #参照するパスワードファイルのパス 
Require valid-user
```
4. cd /etc/apache2
5. sudo vi apache2.conf
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

<Directory /var/www/html> # /var/www/html下の.htaccessファイルの設定を読み込む記述を追加
	AllowOverride AuthConfig
</Directory>
```
6. sudo touch .htpasswd
7. sudo htpasswd -c .htpasswd user1 # ユーザー[user1]とパスワードを設定する
8. sudo systemctl restart apache2

ブラウザからサーバが立ち上がっている確認する
http://[ip-address]
