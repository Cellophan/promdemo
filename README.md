
https://prometheus.io/docs/introduction/install/#using-docker

https://5pi.de/2015/01/26/monitor-docker-containers-with-prometheus/

https://www.digitalocean.com/community/tutorials/how-to-install-prometheus-using-docker-on-ubuntu-14-04



docker run --rm -ti -v /sys/fs/cgroup:/cgroup -v /var/run/docker.sock:/var/run/docker.sock --name container-exporter prom/container-exporter
#docker run --rm -ti -p 9090:9090 --name prometheus prom/prometheus


docker run --rm -ti -p 9090:9090 \
	-v $PWD/prometheus-data/prometheus.yml:/etc/prometheus/prometheus.yml \
	--name prometheus \
	--link container-exporter:container-exporter \
	prom/prometheus

