### サーバ側の設定
1. sudo apt install vsftpd
2. cd /etc/vsftpd
3. sudo vi vsftpd.conf
```
listen=NO
```
4. sudo systemctl restart vsftpd

### クライアント側の設定
1. sudo apt install ftp
2. ftp [サーバ側IPアドレス]
※ 求められるユーザー名、パスワードはサーバ側のもの
