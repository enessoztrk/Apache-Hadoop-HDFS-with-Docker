### 1. Start Hadoop-YARN-Hive
- Assuming already started

### 2. Terminal-1: Start spark-shell in yarn mode  
```
pyspark --master yarn
``` 

### 3. Resource manager UI

http://localhost:8088

### 4. Terminal-2 yarn cli 
List yarn applications  
```
docker exec -it cluster-master bash
yarn application -list
```

### 5. Status of application  
```
yarn application -status application_1600195619400_0002
```

### 6. Logs of yarn application
- Save logs in a file
```
yarn logs -applicationId application_1600195619400_0002 > yarnApp_002_logs
```

- Read with less
```
less yarnApp_002_logs
```

### 7. yarn cli -all -list
List all running nodes  
```
yarn node -all -list
 ```

### 8. yarn cli node -status  
See the status of node  
```
yarn node -status cluster-slave-2:43749
```

### 9. Close pyspark
`exit() `