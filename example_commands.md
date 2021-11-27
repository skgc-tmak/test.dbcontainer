# build & up  

```
$ docker-compose up -d  
```

```
$ docker-compose ps  
```

```
       Name                     Command             State                 Ports               
----------------------------------------------------------------------------------------------
mysql8_db-testing_1   docker-entrypoint.sh mysqld   Up      3306/tcp, 33060/tcp               
mysql8_db_1           docker-entrypoint.sh mysqld   Up      0.0.0.0:13306->3306/tcp, 33060/tcp
$ docker-compose exec db mysql -V
mysql  Ver 8.0.16 for Linux on x86_64 (MySQL Community Server - GPL)
```

# dbコンテナのmysqlへログイン  

```
$ docker-compose exec db bash -c 'mysql -u${MYSQL_USER} -p${MYSQL_PASSWORD} ${MYSQL_DATABASE}'
```

# 文字コードの設定  

```
mysql> show variables like '%char%';
+--------------------------+--------------------------------+
| Variable_name            | Value                          |
+--------------------------+--------------------------------+
| character_set_client     | utf8mb4                        |
| character_set_connection | utf8mb4                        |
| character_set_database   | utf8mb4                        |
| character_set_filesystem | binary                         |
| character_set_results    | utf8mb4                        |
| character_set_server     | utf8mb4                        |
| character_set_system     | utf8                           |
| character_sets_dir       | /usr/share/mysql-8.0/charsets/ |
+--------------------------+--------------------------------+
8 rows in set (0.01 sec)
```

# ユーザー一覧(rootユーザーで実行してます)  

```
mysql> select Host, User from mysql.user;
+-----------+------------------+
| Host      | User             |
+-----------+------------------+
| %         | homestead        |
| %         | root             |
| localhost | mysql.infoschema |
| localhost | mysql.session    |
| localhost | mysql.sys        |
| localhost | root             |
+-----------+------------------+
6 rows in set (0.00 sec)  

```

# mysql CLI の終了  

```
mysql> quit  
```  


# MySQLのデータを初期化 

```
$ docker-compose down --volumes
$ docker-compose up -d
```

down コマンド時に --volumes オプションを付けるとコンテナと名前付きボリュームの削除が行えます。
up コマンドで再びコンテナを作成すれば初期化された綺麗なdbコンテナを使えます。