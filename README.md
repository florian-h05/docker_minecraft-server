# Run a Minecraft server in Docker

### Run a Minecraft Java server in Docker with a RCON web console to manage the server.
***
![Image text](https://www.minecraft.net/etc.clientlibs/minecraft/clientlibs/main/resources/img/header/logo.png)
***
## Table of Contents
1. [General Info](#general-info)
2. [Technologies](#technologies)
3. [Installation](#installation)

### General Info
***
This project uses a docker-compose.yml file and an .env file to start a Minecraft Java server in Docker with a web based managment over an RCON console.



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
* create a ```minecraft``` and a ```rcon``` folder inside this folder
* find out the paths, e.g. on Windows ```D:\\Docker-Data\mcserver\minecraft``` and ```D:\\Docker-Data\mcserver\rcon```
* download the ```docker-compose.yml``` and the ```.env``` files
* paste the minecraft path and the rcon path behind ```MC_PATH``` and ```RCON_PATH```

```
MC_PORT= Minecraft server port, e.g. 10001
MC_RCONPASS= password
MC_PATH= e.g. D:\\Docker-Data\mcserver\mcserver
RCON_PATH= e.g. D:\\Docker-Data\mcserver\rcon
RCON_WEBPORT= RCON web interface port, e.g. 11001
RCON_SOCKETPORT= RCON web interface socket port, e.g. 12001
RCON_USER= username
RCON_PASS= password
```
* when selecting your ports, **do not** use common ports, e.g. 80 HTTP or 443 HTTPS
* after filling in your data, you **must not leave a blank** after the ```=``` sign
* example:
```
MC_PORT=10001
MC_RCONPASS=letmein
MC_PATH=D:\\Docker-Data\mcserver\mcserver
RCON_PATH=D:\\Docker-Data\mcserver\rcon
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
* **congratulations!** Now your Minecraft server should be running under the ```MC_PORT``` and you can access the web interace under http://localhost:```RCON_WEBPORT```
