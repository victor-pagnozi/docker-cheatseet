# Docker - Useful Commands

## Containers

- Open a shell in a container on:
	- `docker exec -it <container_name> <shell>`

## Stop and Clear

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
- Stop all containers
	- `docker stop $(docker ps -a -q)`
- Remove all instances
	- `docker rm $(docker ps -a -q)`
- Stop All Volumes
	- `docker volume prune`

## Scan

- Install the Docker Scan Login
	- `sudo apt-get update && apt-get install docker-scan-plugin`
- Login 
	- `docker login`
- Scan the image
	- `docker scan`
- Get a detailed scan report
	- `docker scan --file PATH_TO_DOCKERFILE DOCKER_IMAGE (docker scan --file Dockerfile docker-scan:e2e)`

## Build and Up
- Up Relay
	- `docker-compose -f docker-compose.yml -f docker-compose.dev.yml up -d`
	- `docker-compose -f docker-compose.yml -f docker-compose.dev.yml -f docker-compose.dev.stream.yml up -d`
- Build normal
	- `docker-compose build`
- Build and Up
	- `docker-compose up --build`
- BUild and up a specific image
	- `docker-compose up -d --no-deps --build <service_name>`

## Logs
- Show the more recent logs lines
	- `docker logs --since 30s -f <container_name_or_id>`
- Put a number of lines to limit
	- `docker logs --tail 20 -f <container_name_or_id>`
- Delete the logs on a Docker for Linux install
	- `echo "" > $(docker inspect --format='{{.LogPath}}' <container_name_or_id>)`

## Show Environment Variables
- Show
	- `docker exec -it <container_name> bash -c 'export'`
- List Environment Variables
	- `docker exec relay-backend printenv`

## Others
- Redis
	- `docker exec -it redis /bin/ash`

Link: https://www.macoratti.net/19/02/dock_limp1.htm
