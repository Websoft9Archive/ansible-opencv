# 服务启停

使用由Websoft9提供的 OpenCV 部署方案，可能需要用到的服务如下：

### OpenCV

```shell
sudo systemctl start opencv-server
sudo systemctl stop opencv-server
sudo systemctl restart opencv-server
sudo systemctl status opencv-server

# you can use this debug mode if OpenCV service can't run
opencv-server console
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
