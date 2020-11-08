# ns3-docker

After cloning:

```
$ brew install wget
$ make
```

It may be better to allocate more than 5GB of RAM to docker. This will take about an hour.
Then set up the necessary tools.

```
// in window No. 1
$ socat TCP-LISTEN:6000,reuseaddr,fork UNIX-CLIENT:\"$DISPLAY\"

// in window No. 2
$ open -a XQuartz
$ $ lsof -i TCP:6000
COMMAND  PID         USER   FD   TYPE             DEVICE SIZE/OFF NODE NAME
socat   2141 reishimitani    5u  IPv4 0xc7cb87d045d395a1      0t0  TCP *:6000 (LISTEN)
```

Finally run the container.

```
$ make run
docker run --rm -it -v `pwd`/ns-allinone-3.30/ns-3.30/src/:/usr/ns3/ns-3.30/src -e DISPLAY=docker.for.mac.host.internal:0 docker-ns3-30
root@2f8a9dd3266e:/usr#
```

To run a simple example:

```
root@2f8a9dd3266e:/usr# cd ns3/ns-3.30
root@2f8a9dd3266e:/usr# ./waf --pyrun src/flow-monitor/examples/wifi-olsr-flowmon.py --vis 

```
