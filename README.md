# load-balancer-tests

Test: Nginx load balancing Docker containers:

Building dummy-servers images and running the containers:
```shell
docker build -t /nginx/dummy-server1/
docker run -d -P dummy-server1
```
```shell
docker build -t /nginx/dummy-server2/
docker run -d -P dummy-server2
```

Inspect the IP of the dummy-servers
```shell
docker ps
docker inspect <dummy-server1-container-name> | grep -i ipa
docker inspect <dummy-server2-container-name> | grep -i ipa
```

We should change the IPs in the upstream file
```shell
vim nginx/load-balancer/conf.d/app.conf
...
upstream app {
	server <dummy-server1-IP>:8000;
        server <dummy-server2-IP>:8000;
}
```

Building Nginx image and running the container:
```shell
docker build -t /nginx/load-balancer/
docker run -d -P load-balancer
```

Next steps: Use Docker Compose and link the containers in order to avoid inspect containers IPs and changing the upstream file every time

