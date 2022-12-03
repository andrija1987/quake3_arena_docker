# quake3_arena_docker

You run the quake_3_arena_docker with below command !

Happy quake-ing :-)

(you need pak0.pk3 file in the directory for running)

docker-compose up -d

pi@raspberrypi:~/quake3 $ cat docker-compose.yml 
version: '2'

services:
  server:
    image: wouterds/rpi-quake3-server
    restart: unless-stopped
    volumes:
      - ./pak0.pk3:/data/pak0.pk3
      - ./server.cfg:/data/server.cfg
    ports:
      - '27960:27960/udp'
    mem_limit: 64mb
    
    pi@raspberrypi:~/quake3 $ cat server.cfg 
seta sv_hostname "andrija1987/rpi-quake3-server"
seta sv_maxclients 12
seta sv_pure 1
//seta logfile 3
//seta rconpassword "secret"

seta timelimit 15
seta fraglimit 20
//seta capturelimit 8 // CTF limit

seta g_gametype 0 // 0: FFA, 1: Tourney, 2: FFA, 3: TD, 4: CTF
seta g_friendlyFire 0
seta g_teamAutoJoin 0
seta g_teamForceBalance 1
seta g_inactivity 120

// Map cycle
set map1 "map Q3DM1; set nextmap vstr map2"
set map2 "map Q3DM6; set nextmap vstr map3"
set map3 "map Q3DM17; set nextmap vstr map1"
vstr map1

// Bots
seta bot_enable 1
seta bot_nochat 0
seta g_spskill 2
seta bot_minplayers 8

