# Minecraft-Server
Minecraft Server created on a proxmox container using itzg/minecraft-server docker image

# Container Preperation
The containers created using a simple Debian 12 Turnkeycore Container Template found on proxmox
![image](https://github.com/Jasmine-108/Minecraft-Server/assets/151819725/f511884c-b96d-48e7-852a-b9191cf6f81c)

To download Docker onto the container these commands were used

```
apt update && apt upgrade
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
```

Then itzg's docker image was downloaded using the `docker pull` command (source: https://hub.docker.com/r/itzg/minecraft-server)
```
docker pull itzg/minecraft-server
```

# Creating the Docker Compose file
Copying the example files provided by itzg https://github.com/itzg/docker-minecraft-server/tree/master/examples
I edited the needed paramaters in visual studio code on my own PC first
![image](https://github.com/Jasmine-108/Minecraft-Server/assets/151819725/7a3d3c54-e857-495c-8ff7-057fada3b941)


The Cobblemon server also needed port 24454 open to run `simple voice chat` but docker compose only opens tcp ports and not udp
This was fixed by specifying the port was udp 

![image](https://github.com/Jasmine-108/Minecraft-Server/assets/151819725/a5bfe634-5061-49d5-a538-8352e4e888db)

# Starting server on proxmox
The docker compose file was first created using
```
touch docker-compose.yml
```

I then copy and pasted the code from visual studio to proxmox
![image](https://github.com/Jasmine-108/Minecraft-Server/assets/151819725/9f7fc772-5b41-48f3-b4e0-3afa34b7ede2)

To startup the server use the command
```
docker compose up -d
```
to view live logs of the server
```
docker compose logs -f
```
