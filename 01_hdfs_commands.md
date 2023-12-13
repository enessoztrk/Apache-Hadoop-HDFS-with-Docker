## Upgrade docker-compose (for centos_min vm)
```
sudo curl -L "https://github.com/docker/compose/releases/download/v2.17.3/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

## See Namenode web UI
- http://localhost:9870/

## See Resource Manager UI
- http://localhost:8088/

### Connect master
```
docker exec -it cluster-master bash
```

# HSFS Commands
## 1. ls lists 
```
 hdfs dfs -ls /
```


## 2. mkdir 
`hdfs dfs -mkdir -p /user/train/play-hdfs-commands `

## 3. put  
put copies files and folders from lokal to hdfs.  

# 4. mv  
move hdfs files/folder to another directory.

## 5. cp  
copies hdfs files/folders to another directory.

## 6. chown
changes ownership of file/folder.

## 7. chmod
changes access rights of file/folder.

## 8. get
downloads a file/folder form hdfs to local.

## 9. du
shows size of folder.

## 10. rm
deletes file/folder from hdfs.  
For folders `-r`  
For skipping trash `-skipTrash`  

## 11. head, tail, cat to read files.

## 12. health check  
```
hdfs fsck /
Connecting to namenode via http://cluster-master:50070/fsck?ugi=root&path=%2F
FSCK started by root (auth:SIMPLE) from /172.24.0.3 for path / at Fri Sep 15 13:38:03 UTC 2023
.Status: HEALTHY
 Total size:    214162609 B
 Total dirs:    6
 Total files:   1
 Total symlinks:                0
 Total blocks (validated):      2 (avg. block size 107081304 B)
 Minimally replicated blocks:   2 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    1
 Average block replication:     1.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          2
 Number of racks:               1
FSCK ended at Fri Sep 15 13:38:03 UTC 2023 in 15 milliseconds


The filesystem under path '/' is HEALTHY

```

## 13. Fix underreplicated blocks
- Collect under-replicated blocks as a list into a file
```
hdfs fsck / | grep 'Under replicated' | awk -F':' '{print $1}' >> /tmp/under_replicated_files
```
- Fix to replication 1
```
for hdfsfile in `cat /tmp/under_replicated_files`; do echo "Fixing $hdfsfile :" ;  hadoop fs -setrep 1 $hdfsfile; done
```

## 14. User Interface of namenode 
http://localhost:5070/
