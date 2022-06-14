# Docker - Comandos Úteis

## Containers

- Abrir um shell em um container em execução:
	- `docker exec -t -i <container_id> <shell>`

## Limpeza

- Excluir containers com status equivalente a Exited:
	- `docker rm -v $(docker ps -a -q -f status=exited)`
- Remover imagens não utilizadas do cache local:
	- `docker rmi $(docker images -f "dangling=true" -q)`
- Limpar o diretório de volumes (vsf) do docker:
	- `docker run -v /var/run/docker.sock:/var/run/docker.sock -v /var/lib/docker:/var/lib/docker --rm martin/docker-cleanup-volumes`