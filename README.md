# vagrant-docker-php7-mysql

## 環境

- PHP7.3
- MySQL8.0
- nginx
- composer

## 実行手順

- git clone

```
git clone https://github.com/soonoki/vagrant_docker_php7_mysql8.git project_name
```

- vagrant起動

```
vagrant up
```

- vagrant接続

```
vagrant ssh
```

- dockerコンテナ起動

```
cd ~/docker
docker-compose -d 

# 初回のみ
docker-compose -d --build
```

- mysql接続

```
docker-compose exec db mysql -u myproject -p
```

