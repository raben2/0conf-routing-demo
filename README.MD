## Fabio & Consul Demo
======================

Run Fabio and consul stack on your machine for testing

### Requirements
You will need to install docker-engine and docker-compose to run this setup

### Run
`
docker-compose up -d 
`

### Stop
`
docker-compose kill
`

## Delete
`
docker-compose rm -f
`

### Accessing the ui

#### consul

http://localhost:8500/

#### fabio

http://localhost:9998/

### register service with consul
The playbook.yaml ansible will register any application to your consul
you have to define the following parameters

**you will need to install python-consul to use that playbook**

+ application - The name of the app
+ port - the application port
+ admin_port - the admin port for the health check
+ healthcheck - the health check url
+ urlprefix - the routing path for fabio


### register the simpleHTTPServer Docker container

`
ansible-playbook -i hosts ./playbook1.yaml -e application=hello -e port=8080 -e urlprefix=spielwiese.local/ 
`

### register a application with health check

`
ansible-playbook -i hosts ./playbook2.yaml -e application=hello -e port=8080 -e admin_port=9080 -e healthcheck='/system/health?pretty=true' -e urlprefix='www.spielwie.se/' 
`

Now simply add the follwoing line to your /etc/hosts file 

`
127.0.0.1 www.spielwie.se
`

and test the app in your browser