# Docker hadoop yarn spark hive cluster

## Run compose

```bash
docker login

docker pull veribilimiokulu/ubuntu_hadoop_hive_sqoop:2.0

docker-compose up -d
```
### Wait hadoop services start
```commandline
 docker logs -f cluster-master
 
```
## Start Hive Services

```bash
docker exec -it cluster-master bash
```

Note: Only for the first run

```bash  
schematool -initSchema -dbType postgres
```

```bash
$HADOOP_HOME/start-hive.sh
$HIVE_HOME/bin/beeline -u jdbc:hive2://localhost:10000
```
