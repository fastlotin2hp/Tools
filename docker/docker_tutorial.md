
docker ps
docker info
docker ps --format $FORMAT 
docker tag //to change name

# examples

  docker run -ti ubuntu bash -c "sleep 3; echo call done"
  //leaving things in container
    docker run -d -ti ubuntu bash -c "sleep 3; echo call done"
  //multi-tasks running in the same containner
    docker exec -ti container_name bash
  //log
    docker logs container_name
  //stop a container and remove it
    docker kill container_name    //to stop
    docker rm container_name
  //resource Constrain
    docker run --memory
    docker run --cpu-shares
                --cpu-quota
  //reaction if docker die
    docker run --restart always
# templete                
   docker run -ti //human interactive
           -rm //clean up container when it's done
           --name give container a name
           
# Inside container:
    exit or ctrl+D to exit
    ctrl+p then ctrl+q to detach (docker attach cntainer_name to get back to the container)
    
# non root user :
  sudo groupadd docker
  sudo usermod -aG docker $USER
  
# dockers communication via ports

  docker run -p inside-port:outside-port(/TCP or /UCP -p 45679:45679==-p 45679:45679/TCP -p 45679:45679/UDP)
  docker run --rm -ti -p 45678:45678 -p 45679:45679 --name echo-server ubuntu:14.04 bash
  //netcat example
  terminal 1: nc -lp 45678 | nc -lp 45679
  terminal 2: nc localhost 45678 (or nc 10.35.3.24 45678)
  terminal 3: nc localhost 45679
  docker port echo-server
  
# building docker images
  multi-project Docker files
  --multi stage build
  ```dockerfile
  FROM ubuntu:16.04 as builder
  RUN apt-get update
  RUn apt-get -y install curl
  RUN curl https://google.com |wc -c > google-size
  
  FROM alpine
  COPY --from=builder /google-size /google-size
  ENTRYPOINT echo google is this big; cat google-size
  ```
  docker build -t too-big .
  docker build -t google-size .
  ```
  docker run too-big
  docker run google-size
  
  ```
# sharing data between containers
  they inherit one to another until last container ended
  ```bash
  #container 1 (container_name1)
  docker run -ti -v /share-data ubuntu bash 
    echo hello > /share-data/data_file
  
  #container 2
  docker ps -l
  docker run -ti --volumes-from container_name1(container's name(container 1) ubuntu bash
    ls /share-data/
    echo more > /shared-data/data_file2 
  ```
  
# under the hood
  acronym
  
# aws fargate
# aws EKS
# kubernetes engine
  
  
  
  
  
