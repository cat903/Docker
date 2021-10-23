//delete dangling images

- sudo docker rmi $(sudo docker images --filter "dangling=true" -q --no-trunc)

// delete containers that are not used.

- sudo docker ps -a | grep -v Up | awk '{ print $1; }' | xargs sudo docker rm

//delete all containers with none tags.

- sudo docker images | grep none | awk '{ print $3; }' | xargs sudo docker rmi
