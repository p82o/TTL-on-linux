## How to change the default TTL on Linux

To see the current [TTL](https://en.wikipedia.org/wiki/Time_to_live) on your system you can run this command:
```
cat /proc/sys/net/ipv4/ip_default_ttl
```
In most cases it'll be `64`. This is the default value for most Linux systems.

To change the default TTL of TCP/IP packets sent from your Linux computer you can run the following command:
```
sudo sysctl -w net.ipv4.ip_default_ttl=65
```
Or:
```
echo 65 | sudo tee /proc/sys/net/ipv4/ip_default_ttl
```
Or:
```
sudo bash -c 'echo 65 > /proc/sys/net/ipv4/ip_default_ttl'
```
But you have to run one of those commands whenever the computer boots. To make this setting persistent across reboots you could append the following line to the file `/etc/sysctl.d/99_default_ttl.conf`:
```
net.ipv4.ip_default_ttl=65
```
and then run this command:
```
sudo sysctl --system
```
You should do the same with ipv6 instead of ipv4 if you want to change the settings for ipv6 as well.
