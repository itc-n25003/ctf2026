### サーバ側
1. sudo apt install xinetd
2. sudo apt install telnetd
3. cd /etc/xinetd.d
4. sudo vi telnet
```
service telnet
{
	disable = no
	flags = REUSE
	socket_type = stream
	wait = no
	user = root
	server = /usr/sbin/telnetd
	log_on_failure += USERID
}
```
5. sudo systemctl restart xinetd

### クライアント側
1. sudo apt install telnet
2. telnet [サーバ側IPアドレス]
