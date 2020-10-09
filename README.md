# demo-perfsonar-mobile
Simple pscheduler commands and system configs to support mobile perfSONAR testpoints




Presentation Links: 

[Debugging Network Connectivity issues at the Randall Labratory: A case study for Mobile 10GE perfSONAR testpoints](https://docs.google.com/presentation/d/14N-Brebma6jqayN6q5mj8TLDwMZIYUV2yZw5kkcdFCQ/edit?usp=sharing)

[Know Your (perfSONAR) Limits Webinar](https://www.youtube.com/watch?v=UNItTorQqnw)

[perfSONAR Ansible playbook](https://github.com/perfsonar/ansible-playbook-perfsonar)

[SuperMicro E-300-8D](https://www.supermicro.com/en/products/system/Mini-ITX/SYS-E300-8D.cfm)

[YouTube presentation](https://www.youtube.com/watch?v=02YLA24KFCY&feature=youtu.be&t=10)


pscheduler commands:

```
pscheduler task \
  throughput \
  --source 141.213.137.100 \
  --dest 141.213.137.101
```

/etc/sysconfig/network-scripts/ifcfg-bond0

```
DEVICE=bond0
NAME=bond0
TYPE=Bond
BONDING_MASTER=yes
IPADDR=141.213.137.101
PREFIX=29
GATEWAY=141.213.137.97
DNS1=10.10.10.10
DNS2=10.10.5.5
DNS3=8.8.8.8
ONBOOT=yes
BOOTPROTO=none
BONDING_OPTS="mode=1 primary=eno7 miimon=100"
NM_CONTROLLED="no"
MTU=9200
ZONE=public
```

/etc/sysconfig/network-scripts/ifcfg-eno7

```
TYPE=Ethernet
NM_CONTROLLED=no
PROXY_METHOD=none
BROWSER_ONLY=no
BOOTPROTO=none
DEFROUTE=NO
NAME=bond0-slave
UUID=492a8790-8426-4ad6-913e-107e0d557a3c
DEVICE=eno7
ONBOOT=yes
MASTER=bond0
SLAVE=yes
MTU=9200
```
