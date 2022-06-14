# Docker - Useful Commands

## Containers

- Open a shell in a container on:
	- `docker exec -it <container_name> <shell>`

## Cleaning

- Delete containers if they are "Exited":
	- `docker rm -v $(docker ps -a -q -f status=exited)`
- Delete images not used of the local cache:
	- `docker rmi $(docker images -f "dangling=true" -q)`
- Clear the volumes directory of Docker:
	- `docker run -v /var/run/docker.sock:/var/run/docker.sock -v /var/lib/docker:/var/lib/docker --rm martin/docker-cleanup-volumes`
- Remove exited containers, networks not used by at least one container, all dangling images and all dangling build cache
	- `docker system prune`
- Remove exited containers, networks not used by at least one container, all dangling images, all dangling build cache and volumes not used 
	- `docker system prune --all --force --volumes`



Link: https://www.macoratti.net/19/02/dock_limp1.htm
