# Start or Stop the Services

These commands you must know when you using the OpenCV of Websoft9

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
