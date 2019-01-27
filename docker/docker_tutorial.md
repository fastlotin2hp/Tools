
docker ps
docker info
docker ps --format $FORMAT 
docker tag //to change name

--examples
  docker run -ti ubuntu bash -c "sleep 3; echo call done"
  //leaving things in container
  docker run -d -ti ubuntu bash -c "sleep 3; echo call done"
  //


docker run -ti //human interactive
           -rm //clean up container when it's done
           
--Inside container:
    exit or ctrl+D to exit
    ctrl+p then ctrl+q to detach (docker attach cntainer_name to get back to the container)
    
    
--non root user :
  sudo groupadd docker
  sudo usermod -aG docker $USER
