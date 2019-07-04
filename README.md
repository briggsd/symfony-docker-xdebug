## Setup

### Build Docker Containers

```
docker-compose build
```

### Configure XDebug IP address

In the project root directory, copy the `.env` to `.env.local`.  Then update the `DEBUG_IP` parameter to use the local 
IP address.  That is the IP address assigned by your LAN.  For instance, if the IP address of my development workstation is `192.168.1.139` I would update my .env.local 
like the following:
```json
###> xdebug ###
DEBUG_IP=192.168.1.139
###< xdebug###
```

### Start Docker Containers

Once your local env file has been updated, you can start the docker containers by running the following command:

```
docker-compose up -d
```

Once the containers have finished setting up, you should be able to access the site by going to ```http://localhost:8010``` 
in your browser.


