

network (inc rc.conf alias's)
```
/etc/rc.d/netif restart
```
routing
```
/etc/rc.d/routing restart
```
To stop network card (NIC) on-fly:
```
ifconfig network-interface down
```

To start network card (NIC) on fly:
```
ifconfig network-interface up
```

To list down network interface:
```
ifconfig -d
```

To list up network interface:
```
ifconfig -u
```