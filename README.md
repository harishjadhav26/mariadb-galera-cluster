# MariaDB Galera Cluster

***Start the MariaDB Galera Cluster***
```
docker-compose -p galera_cluster up -d

docker-compose -p galera_cluster logs -f
```

***Check the Cluster Status***

```
# Check the galera running status
mysql -u root -h 127.0.0.1 -P 3306 -p -e "show status like 'wsrep_%'"

# Check cluster nodes size
mysql -u root -h 127.0.0.1 -P 3306 -p -e "show status like 'wsrep_cluster_size'"

```

***High Availability already configured with HAProxy***

If you check the above test scenario and try to create DBs on any of the nodes, you would see that the data would automatically sync between the nodes. Which means Availability is achieved.

```
Connect to Loadbalancer VM IP address : 3306 and you should now have a Highly Available MySQL Cluster with Galera.

EX:
<HAProxy SERVERIP>:3306
```

***Check HAPROXY PORT***

```
telnet <HAProxy SERVERIP>:3306

EX:

telnet 192.168.1.4:3306

```

***MariaDB Configuration Use In Application***

```
Connection use in any application like, it may vary application wise:
EX:
mysql://user:pass@192.168.1.4:3306/<DB NAME>
```