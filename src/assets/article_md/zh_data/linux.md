
### Querying last Boot Time
```bash
who -b
```
### list all user 
```bash
who -q
```

### Execute as Administrator
```bash
sudo
```

### Move to Another Directory
```bash
cd 
```

### Clear the Screen
```bash
clear
```

## Resource usage

### Show vram usage
```
watch -n 1 nvidia-smi
```

### Show cpu and ram usage
```
htop
```

### Memory
```bash
# total file's memory
du -sh
# each file's memory
du -h
# each file's memory in the depth 1
du -h --max-depth=1
```



## File Management Commands

### List Files in a Directory
```bash
ls

# Finding a Specific File
ls | grep a_file
```

### Copy Files
#### Copy a_file to b_file
```bash
cp a_file b_file
```

### Move/Rename Files
#### Move a_file to b_file; renaming if in the same location
```bash
mv a_file b_file
```

### Delete Files
```bash
rm a_file

# Use -r parameter to delete directories
rm -r a_folder
```

### Edit File Content
```bash

# Either one can be used
vim file_name
nano file_name
```

### View Files
```bash
cat a_file

# Use when dealing with larger files
less a_file
more a_file
```

## Server Related
### Accessing a Server
```bash
ssh user_name@host_name
```

### Copy from Local to Server
```bash
scp local_path user_name@host_name:server_path
```

### Copy from Server to Local
```bash
scp user_name@host_name:server_path local_path
```