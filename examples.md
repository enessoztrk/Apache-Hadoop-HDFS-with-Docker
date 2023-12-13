### Q-1: 
- Setup multinode hadoop with docker compose
- Download and put `https://raw.githubusercontent.com/erkansirin78/datasets/master/Wine.csv` dataset in hdfs `/user/root/hdfs_odev` directory.

`docker-compose up -d`
`docker exec -it cluster-master bash`
`curl -L https://raw.githubusercontent.com/erkansirin78/datasets/master/Wine.csv -o Wine.csv`
`hdfs dfs -mkdir -p /user/root/hdfs_odev`
`hdfs dfs -put Wine.csv /user/root/hdfs_odev/`

### Q-2:
- Copy this hdfs file `/user/root/hdfs_odev/Wine.csv` to `/tmp/hdfs_odev` hdfs directory.

`hdfs dfs -cp /user/root/hdfs_odev/Wine.csv /tmp/hdfs_odev/`

### Q-3:
- Delete `/tmp/hdfs_odev` directory with skipping the trash. 

`hdfs dfs -rm -r -skipTrash /tmp/hdfs_odev`

### Q-4:
-  Explore `/user/root/hdfs_odev/Wine.csv` file from namenode web ui.  

`http://localhost:9870/explorer.html#/user/root/hdfs_odev`
