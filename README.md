This is the Nsotr project for supply chain. This project contains 2 relays that have been chosen to parse data in 
a supply chain environment.


### [NIPs](https://github.com/nostr-protocol/nips) that are suppoereted by this relay network

- [x] NIP-01: Basic protocol for all supply chain needs
- [x] NIP-02: Contact list and petnames in identifying supply chain users.
- [x] NIP-04: Encrypted Direct messaging for supply chain customers and merchants
- [x] NIP-09: Event deletion
- [x] NIP-11: Relay information document
- [x] NIP-12: Generic tag queries
- [x] NIP-15: End of Stored Events Notice
- [x] NIP-16: Event Treatment
- [x] NIP-20: Command Results
- [x] NIP-22: Event `created_at` Limits
- [x] NIP-26: Delegated Event Signing
- [x] NIP-28: Public Chat
- [x] NIP-33: Parameterized Replaceable Events
- [x] NIP-40: Expiration Timestamp
- [x] NIP-42: Authentication of clients to relays
- [x] NIP-45: Counting results. [experimental](#count)
- [x] NIP-50: Keywords filter. [experimental](#search)



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

## Check the SQlite database of nostr-rs-relay

make sure you have sqlite installed in your computer

```shell
cd \Nostr\nostr-rs-relay
```
you can look in the databse using the follwing commands

NOTE : ⚠️ carefull with this one as you might damage the db

```shell
sqlite3 nostr.db

sqlite> .databases
sqlite> .tables
sqlite> select * from event;
sqlite> select count(*) from event;
```

Connect your client
If you made it so far, congrats !!

## Connecting to a client

These relays are now running in this host system and can be accessed only though the host system.⚠️ So any clients that needs to be conncted to this relay needs to be in the host computer and cannot be accessed though the internet. 

Now is time to connect your client and see it at work !!

connect your client to ws://localhost:7001/ or ws://localhost:7001/. you can add the client to other relays you might have put in the projct and would be aviable in a similar way with the ports you have setup. Send some messages, see the log get them in  real time and find them in the database.

## Adding additional relays

You can add additional relays to this relay network. Simply add the relay into the notr main folder and create the docker file within the new relay folder. Then add your relay to the all the executable methods 

Docker compose file goes as follows, you can change the names of the rlays as you wish and the name of the docker files as you wish as well. 

```shell
version: '3'

services:
  nostr-rs-relay:
    build: ./nostr-rs-relay
    ports:
      - "7001:8080"

  rnostr:
    build: ./rnostr
    ports:
      - "7002:8080"

  relay3:
    build: ./path_to_relay3_dockerfile
    ports:
      - "7003:8080"

  relay4:
    build: ./path_to_relay4_dockerfile
    ports:
      - "7004:8080"
```
## Lisence 


## External Documentation and Links

Add setup guide for external web access 