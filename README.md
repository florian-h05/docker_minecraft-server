# Run a Minecraft server in Docker

### Run a Minecraft Java server in Docker with a RCON web console to manage the server.
***
![Image text](https://www.minecraft.net/etc.clientlibs/minecraft/clientlibs/main/resources/img/header/logo.png)
***
## Table of Contents
1. [General Info](#general-info)
2. [Technologies](#technologies)
3. [Installation](#installation)
4. [FAQs](#faqs)

### General Info
***
This project uses a ```docker-compose.yml``` file and an ```.env``` file to start a Minecraft Java server in Docker with a web based management over an RCON console.



## Technologies
***
A list of technologies used within the project:
* [Docker Desktop](https://www.docker.com/get-started)
* [Docker Compose](https://docs.docker.com/compose/): Version 3.9
* [Docker: itzg/minecraft-server](https://hub.docker.com/r/itzg/minecraft-server):latest
* [Docker: itzg/rcon](https://hub.docker.com/r/itzg/rcon):latest

## Installation
***
Following prerequisites have to be met:
* [Docker Desktop](https://www.docker.com/get-started) installed and running
* Access to the command line, e.g. PowerShell on Windows

A little intro about the installation. 
* create a folder
* create a ```mcserver1``` and a ```rcon``` folder inside this folder
* download the ```docker-compose.yml``` and the ```.env``` files
* **do not** download the ```docker-compose.override.yml```
* for more information about Minecraft server types, visit: [itzg/minecraft-server documentation](https://github.com/itzg/docker-minecraft-server#readme)

```
MC_PORT=                Minecraft server port, e.g. 10001
MC_RCONPASS= password
MC_MAXMEMORY=           memory usage limit, e.g. 2G for 2 gigabytes
MC_TYPE=                Server Type, e.g. PAPER
MC_RCON_PORT=25575      no change needed when running only one Minecraft server
RCON_WEBPORT=           RCON web interface port, e.g. 11001
RCON_SOCKETPORT=        RCON web interface socket port, e.g. 12001
RCON_USER= username
RCON_PASS= password
```
* when selecting your ports, **do not** use common ports, e.g. 80 HTTP or 443 HTTPS
* ignore the rest of the ```.env``` file which is not shown here
* after filling in your data, you **must not leave a blank** after the ```=``` sign
* example:
```
MC_PORT=10001
MC_RCONPASS=password
MC_MAXMEMORY=2G
MC_TYPE=PAPER
MC_RCON_PORT=25575
RCON_WEBPORT=11001
RCON_SOCKETPORT=12001
RCON_USER=admin
RCON_PASS=admin
```
* when you have prepared all files, log in to your console:
```
$ cd /path-of-your-folder or on Windows D:\\path-to-your-folder
$ docker-compose up -d
```
* **congratulations!** Now your Minecraft server should be running under the ```MC_PORT``` and you can access the web interface under http://localhost:```RCON_WEBPORT```

### Install multiple servers
***

* Follow the steps above, but
* additionally create a ```mcserver2``` folder -- replace the number with the server number
* download the ```docker-compose.override.yml```
* now the rest of the ```.env``` file is important:
```
# for adding more servers -- docker-compose.override.yml is needed

MC_PORT2=10002          increase the port number with the server number
MC_RCONPASS2=letmein
MC_MAXMEMORY2=2G
MC_TYPE2=PAPER
MC_RCON_PORT2=25576     increase the port number with the server number
```
* change the ports and the paths according to your server number!!
* if this is not your second server, but your third... , you also need to replace the number at the end of the service name in ```docker-compose.override.yml```
```
version: '3.9'

services:
  minecraft2: # replace this number with your server number
    ports:
    ...
```
* when you have prepared all files, log in to your console:
```
$ cd /path-of-your-folder or on Windows D:\\path-to-your-folder
$ docker-compose up -d
```
* **congratulations!** Now your second or third... Minecraft server should be running
* add the server to the rcon web interface with the hostname set in the ```.env``` file

## FAQs
***
A list of frequently asked questions

### How can I change the port settings?
Change the ports in the ```.env``` file and run in your terminal:
```
$ cd /path-of-your-folder or on Windows D:\\path-to-your-folder
$ docker-compose up
```
### How can I update the containers?
To update your containers, run this in your terminal:
```
$ docker pull itzg/minecraft-server:adopt14
$ docker pull itzg/rcon:latest
$ docker container ls
```
Now search the names of your containers, e.g. ```mcserver_minecraft_1``` and ```mcserver_rcon_1``` . You can also delete them in the Docker Desktop app.
```
$ docker rm CONTAINER_1
$ docker rm CONTAINER_2
$ cd /path-of-your-folder or on Windows D:\\path-to-your-folder
$ docker-compose up -d
```
### How to change the server's settings?
Open your path e.g. ```D:\\Docker-Data\mcserver\mcserver1``` folder and open ```server.properties``` with a text editor. For information about the settings, please visit [Minecraft Gamepedia (German)](https://minecraft-de.gamepedia.com/Server.properties) or [Minecraft Gamepedia (English)](https://minecraft.gamepedia.com/Server.properties).


### Which commands can I use in the RCON web interface?
1. Type ```help``` in the RCON web console.
2. Search for help on [Google](https://google.com) or visit [this website](https://www.ign.com/wikis/minecraft/Admin_and_Server_Commands).

### How can I run multiple Minecraft Servers?
Just follow the [Installation](#installation) documentation, but choose **other ports** and create **new, different folders**.