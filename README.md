
Seedlink Server with slarchive service in Docker

<a href="https://github.com/nikosT/seedlink-with-slarchive-docker/blob/main/seedlink-slarchive.png">
<img src="https://github.com/nikosT/seedlink-with-slarchive-docker/blob/main/seedlink-slarchive.png" width="80%"/>
</a>
<br/><br/>


There are two modules `SeedLink` and `slarchive` in a dockerized environment. 

### SeedLink
Use `SeedLink` in order to expose the data that are in the `./archive_encrypt` (see https://github.com/nikosT/seedlink-with-slarchive-docker/blob/main/docker-compose.yml#L40) directory via a SeedLink protocol

### Slarchive
Use `Slarchive` in order to retrieve real-time data from an external SeedLink server and save them in the `./archive` (see https://github.com/nikosT/seedlink-with-slarchive-docker/blob/main/docker-compose.yml#L16) directory (e.g. for further processing).

## Prerequisites
* Docker with docker compose

## Configuration
In general you will only need to change the `./archive` and the `./archive_encrypt` paths (see below). 
For more custom things, you might need to change:

For `SeedLink`, the file: https://github.com/nikosT/seedlink-with-slarchive-docker/blob/main/seedlink/ring.conf
For `Slarchive`, the files: https://github.com/nikosT/seedlink-with-slarchive-docker/blob/main/slarchive/seiscomp3/slarchive.cfg and https://github.com/nikosT/seedlink-with-slarchive-docker/blob/main/slarchive/seiscomp/var/lib/slarchive/slarchive.streams


## Run

```bash
docker compose up
```

You can run each module seperately
```bash
docker compose up seedlink
```
or
```bash
docker compose up slarchive
```

Both `./archive` and `./archive_encrypt` are mounted as volumes so data inside them can be directly accessed by the host.
