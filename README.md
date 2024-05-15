This is the Nsotr project for supply chain. This project contains 3 relays that have been chosen to parse data in 
a supply chain environment.

Supports most applicable NIPs: 1, 2, 4, 9, 11, 12, 15, 16, 20, 22, 28, 33, 40

## Quick Start (using docker)

Make sure docker is installed in your system and updated 

The provided docker compose file will build and complile the project.IF you wish to change the bind mounts you can edit the bind mounts in the docker-compose.yml file to the bind mounts you want. Currently both the relays (containers) have been bound to 8080 port and the host is connected to 7001 (nostr-rs-relay) and 7002(rnostr) relay. 

The command below will create docker images and start both the containers (make sure to cd into the project)

```shell
docker-compose up -d
```

All the relays should be up and running now, you can access the relays in your browser at http://localhost:7001/
and http://localhost:7002/

following command will stop all the realays 

```shell
docker-compose down
```

if you want to stop and remove all volumes you can use the -v flag 

```shell
docker-compose down -v
```

## Quick Start using Bash 

cd into the directory for the nostr project 

Make sure your Bash has executable permissions. If it doesn't, you can grant execute permissions using the chmod command:

```shell
chmod +x build_and_run.sh
```

Run the bash script 

./docker_setup.sh



"# nostr" 
