# Start or Stop the Services

These commands you must know when you using the JumpServer of Websoft9

## JumpServer

```shell
sudo systemctl start jumpserver-server
sudo systemctl stop jumpserver-server
sudo systemctl restart jumpserver-server
sudo systemctl status jumpserver-server

# you can use this debug mode if JumpServer service can't run
jumpserver-server console
```

## JumpServer

```shell
sudo systemctl start jumpserver-server
sudo systemctl stop jumpserver-server
sudo systemctl restart jumpserver-server
sudo systemctl status jumpserver-server

# you can use this debug mode if JumpServer service can't run
jumpserver-server console
```

### MySQL

```shell
sudo systemctl start mysql
sudo systemctl stop mysql
sudo systemctl restart mysql
sudo systemctl status mysql
```

### Redis

```shell
systemctl start redis
systemctl stop redis
systemctl restart redis
systemctl status redis
```