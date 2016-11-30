docker-nginx-consul-template
============================

A Consul Template powered Nginx docker container.

`docker run stakater/nginx-with-consul-template:latest`

This image is intended to be run together with Consul and Consul-Template in order to get transparent and dynamic load balancing as new containers are started/stopped.

The daemon consul-template queries a Consul instance and updates any number of specified templates on the file system. As an added bonus, consul-template can optionally run arbitrary commands when the update process completes. 

Nginx is popular open source web server, reverse proxy, and load balancer

`docker run -p 8080:80 -d --name nginx --volume /home/core/templates:/templates --link consul:consul stakater/nginx-with-consul-template:latest`

consul-template -consul=$CONSUL_URL -template="/templates/service.ctmpl:/etc/nginx/conf.d/service.conf:service nginx reload"

consul-template -consul=$CONSUL_URL -template="/templates/service.ctmpl:/etc/nginx/conf.d/service.conf" -exec="service nginx reload"

The current issue is with nginx!
