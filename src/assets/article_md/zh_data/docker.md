
## Quick Step for using docker

### Step1. write down dockerfile
* #### new a 'dockerfile' file and write down the building step.


### Step2. build images
```bash
docker build -t <image_name> .
```

### Step3. run container
```bash
docker run -d --name <container_name> -p 8080:80 <image_name>
# -d: run in background
# --name: Optional
# -p: <outside> 8080 -> 80 <docker container port>
```

## Useful code

### check images
```bash
docker images
docker image list
``` 

### check container
```bash
# only show running container
docker ps
# all container
docker ps -a
```

### into docker container
```bash
docker exec -it <container_name> bash
```

### check space
```bash
docker system df
```

### docker copy
```bash
docker cp <file_name> <container_name>:<docker_path>
```