
# Create Snapshot
```
sudo -u hdfs hdfs dfs -mkdir /precious
sudo -u hdfs hdfs dfs -copyFromLocal install-bootcamp-master.zip /precious
sudo -u hdfs hdfs dfsadmin -allowSnapshot /precious
sudo -u hdfs hdfs dfs -createSnapshot /precious sebc-hdfs-test

sudo -u hdfs hdfs dfs -ls /precious/.snapshot
->drwxr-xr-x   - hdfs supergroup          0 2019-02-12 10:56 /precious/.snapshot/sebc-hdfs-test
```
# Delete HFS not its possible
```
sudo -u hdfs hdfs dfs -rm -R /precious/*
rm: Failed to move to trash: hdfs://CDH-HA/precious: The directory /precious cannot be deleted since /precious is s           napshottable and already has snapshots
```
# Restore Snapshot
```
sudo -u hdfs hdfs dfs -cp -ptopax /precious/.snapshot/sebc-hdfs-test /precious/
sudo -u hdfs hdfs dfs -ls /precious
Found 1 items
-rw-r--r--   3 hdfs supergroup    1019399 2019-02-12 10:55 /precious/install-bootcamp-master.zip
```
