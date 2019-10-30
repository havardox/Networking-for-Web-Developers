# Networking-for-Web-Developers

## Linux virtuaalmasina paigaldamine (Vagrant) ##

```
mkdir networking
cd networking
vagrant init ubuntu/trusty64
vagrant up
```

## Linux'i käivitamine ##

```
vagrant ssh
```

## Linux laienduste installeerimine ##


```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install netcat-openbsd tcpdump traceroute mtr
```

## Network asjade testimine ##

```
ip addr show eth0
ip route show
ping -c3 8.8.8.8
host -t aaaa google.com
host -t mx udacity.com
printf 'HEAD / HTTP/1.1\r\nHost: www.udacity.com\r\n\r\n' | nc www.udacity.com 80
sudo tcpdump -n -c5 -i eth0 port 22
traceroute www.udacity.com
mtr www.udacity.com
q
printf 'HEAD / HTTP/1.1\r\nHost: en.wikipedia.org\r\n\r\n' | nc en.wikipedia.org 80
printf 'HEAD / HTTP/1.1\r\nHost: www.google.com\r\n\r\n' | nc www.google.com 80
man nc
q
Teise Linux masina käivitamine: vagrant ssh
Masin 1: nc -l 3456
Masin 2: nc localhost 3456
Masin 2: CTRL + d
Masin 1: nc -l 65535
Masin 2: nc localhost 65535
Masin 2: CTRL + d
Masin 1: nc -l 1024
Masin 2: nc localhost 1024
Masin 2: CTRL + d
Masin 1: nc -l 2000
Masin 2: nc -l 2000
Masin 1: CTRL + c
sudo lsof -i
hostname -i
printf 'HTTP/1.1 302 Moved\r\nLocation: https://www.eff.org/' | nc -l 2345
ping google.com
CTRL + c
host www.reddit.com
ip addr show
ip route show default
ping <Linux masina IP aadress>
Masin 2: sudo tcpdump -n host 8.8.8.8
Masin 1: ping -c3 8.8.8.8
Masin 2: CTRL + c
Masin 2: sudo tcpdump -n port 53
Masin 1: ping yahoo.com
Masin 1: CTRL + c
Masin 2: CTRL + c
Masin 2: sudo tcpdump -n host example.net
Masin 1: printf 'HEAD / HTTP/1.1\r\nHost: example.net\r\n\r\n' | nc example.net 80
Masin 2: CTRL + c
Masin 2: sudo tcpdump port 12345
Masin 1: nc www.udacity.com 12345
Masin 2: CTRL + c
traceroute reddit.com
```
