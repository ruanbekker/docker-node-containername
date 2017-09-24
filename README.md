# docker-node-containername
Nodejs Application for Docker to Print Hostnames

## Usage:

Launch the Stack:

```
$ git clone https://github.com/ruanbekker/docker-node-containername
$ cd docker-node-containername
$ docker stack deploy -c docker-compose.yml node
```

List the Services in the Stack:

```
$ docker stack ls
NAME                SERVICES
node                2
```

List the Tasks in the Stack:

```
$ docker stack ps node
ID                  NAME                  IMAGE                                 NODE     DESIRED STATE       CURRENT STATE            ERROR               PORTS
l5ryfaedzzaq        node_loadbalancer.1   dockercloud/haproxy:latest            dsm-01   Running             Running 40 minutes ago
c8nrrcvek79h        node_node-app.5       rbekker87/node-containername:latest   dsm-01   Running             Running 40 minutes ago
dqii18b2q5nn        node_node-app.10      rbekker87/node-containername:latest   dsm-01   Running             Running 40 minutes ago
vkpw2rugy0ah        node_node-app.11      rbekker87/node-containername:latest   dsm-01   Running             Running 40 minutes ago
mm88nvnvy5lg        node_node-app.12      rbekker87/node-containername:latest   dsm-01   Running             Running 40 minutes ago
oyx8rfqc1xl2        node_node-app.16      rbekker87/node-containername:latest   dsm-01   Running             Running 41 minutes ago
```

Test out the Service:

```
$ curl -XGET http://127.0.0.1/
My Hostname: a6e34246e73b
$ curl -XGET http://127.0.0.1/
My Hostname: 5de71278be38
$ curl -XGET http://127.0.0.1/
My Hostname: e0b7316fdd51
```

Remove the Stack:

```
$  docker stack rm node
Removing service node_loadbalancer
Removing service node_node-app
Removing network node_nodenet
```

