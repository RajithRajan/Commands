### To get the list of java process
```
jps
```



### read a file from hdfs
```
hdfs dfs -cat /file/path
```

### Copy file from local fs to hdfs
```
hdfs dfs -copyFromLocal /from/local/fs/path /to/hdfs/path
```

### Copy file to local
```
hdfs dfs -copyToLocal  /from/hdfs/path /to/local/fs/path
```
### count the number of directories, files, and bytes under the paths that match the specified file pattern
```
hdfs dfs -count /path
```

### Copy file 
```
hdfs dfs -cp /src/path /dest/path
```

### to check the file size
```
hdfs dfs -du /file-dir/path
```

### Empty trash
```
hdfs dfs -expunge
```

### To get the HDFS Health
```
hdfs fsck /
```

### Copy file to local
```
hdfs dfs -get  /from/hdfs/path /to/local/fs/path
```

### Help command
```
hdfs dfs -help
```

### List all the HDFS file/directory
```
hdfs dfs -ls
```
### To create a directory
```
hdfs dfs -mkdir /dir/name
```
### Move files
```
hdfs dfs -mv /from/path /to/path
```

### Copy data from the local system to hdfs
```
hdfs dfs -put /from/path /to/path
```

### Remove the file from HDFS
```
hdfs dfs -rm /file/path
```
Remove the dir with file from HDFS
```
hdfs dfs -rm-r  /dir/path
```

### Remove the dir from HDFS
```
hdfs dfs -rmdir  /dir/path
```

### Output file in text format
```
hdfs dfs -text /file/path
```

### to create a file
```
hdfs dfs -touchz /file/path
```
### To file help for individual  command
```
hdfs dfs -usage <command>
hdfs dfs -usage mkdir
```

### To get the version of Haddop
```
hadoop version
```
