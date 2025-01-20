# Unifi Controller
<div align="left">
<img src="https://simpleicons.org/icons/ubiquiti.svg" height="40" alt="ubiquiti logo"  />
<img width="12" />
<img src="https://simpleicons.org/icons/docker.svg" height="40" alt="docker logo"  />
<img width="12" />
</div>

## Image : 
```<bash>
lscr.io/linuxserver/unifi-controller:latest
```
## Environement : 
```<bash>
      - PUID=1000
      - PGID=1000
      - TZ=Etc/UTC
```
|ENV|Variable|
|---|--------|
|TZ|Time Zone|
|PUID|ID du user root|
|PGID|ID du groupe root|

<a href="https://en.wikipedia.org/wiki/List_of_tz_database_time_zones#List" target="_blank">Time Zone List</a>
## Ports : 
|Ports & Protocol|Utilisations|
|----------------|------------|
|8443|Interface web Admin|
|3478 udp|Unifi STUN port|
|10001 udp|Requis pour découvrire les AP sur le réseau|
|8080|Communications des appereils|
|1900|Requis pour découvrir le controlleur dans un réseau L2|
|8843|HTTPS portail - Guest|
|8880|HTTP portail - Guest|
|6789|pour les test de début mobile|
|5514|Remote Syslog Port|

```<bash>
      - 8443:8443
      - 3478:3478/udp
      - 10001:10001/udp
      - 8080:8080
      - 1900:1900/udp #optional
      - 8843:8843 #optional
      - 8880:8880 #optional
      - 6789:6789 #optional
      - 5514:5514/udp #optional
```
## Volumes :

"- Source Host":/config

```<bash>
    - /mnt/storage/unifi:/config
```
## Restart :
```<bash>
  restart: unless-stopped
```
## Docker Compose 
```<bash>
services:
  unifi-controller:
    image: lscr.io/linuxserver/unifi-controller:latest
    container_name: unifi-controller
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Etc/UTC
    volumes:
      - /mnt/storage/unifi:/config
    ports:
      - 8443:8443
      - 3478:3478/udp
      - 10001:10001/udp
      - 8080:8080
      - 1900:1900/udp #optional
      - 8843:8843 #optional
      - 8880:8880 #optional
      - 6789:6789 #optional
      - 5514:5514/udp #optional
    restart: unless-stopped
```
