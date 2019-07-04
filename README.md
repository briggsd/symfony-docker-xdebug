## Docker Setup & Configuration

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

At this point you should be able to place a breakpoint within a script to begin the debugging process.  For instance, 
navigate to `public/index.php` and place a breakpoint on line 19 and then reload the browser page.  PhpStorm should now 
pause the script at your breakpoint.

## PhpStorm Setup & Configuration

Defaults should mostly work here although it can be helpful to double check them.  Options like Force break at first line 
can also be enabled/disabled to your liking.

### Listening for debug connections

You can start/stop listening for debug connections by going to `Run > Start/Stop Listening for debug connections`.  This 
action should also be available via the toolbar with the same telephone icon.  If the icon has a red circle, it indicates 
you are currently NOT listening for debug connections

### Settings > Language & Frameworks > PHP > Debug

#### Xdebug

* Debug port: 9000
* Check - Can accept external connections
* Check - Force break at first line when no path mapping is specified
* Check - Force break at first line when a script is outside of project






