Docker Get Started
==================

Docker official get started guide.

# Workflow

## Create Docker Machine

```
docker-machine create --driver virtualbox myvm1
docker-machine create --driver virtualbox myvm2
docker-machine ls
```

## Create Docker Swarm

```
docker-machine ssh myvm1 "docker swarm init --advertise-addr <myvm1 ip>"
docker-machine ssh myvm2 "docker swarm join --token <token> <ip>:2377"
docker-machine ssh myvm1 "docker node ls"
```

## Deploy to Swarm
```
eval $(docker-machine env myvm1)
docker stack deploy -c docker-compose.yml getstartedlab
docker stack ps getstartedlab
```

## Tear Down the Swarm

```
docker stack rm getstartedlab
eval $(docker-machine env -u)
```

## Remove Docker Machine

```
docker-machine stop $(docker-machine ls -q)
docker-machine rm $(docker-machine ls -q)
```
