## Deny_all  
```bash
apt install ipset  
/sbin/ipset destroy proxy  
/sbin/ipset flush proxy  
cd /tmp && wget https://github.com/bakup/Serpentarium/raw/main/deny_all_day/last  
/sbin/ipset restore -f -! /tmp/last && rm /tmp/last  
```
#eth1 - external interface(To Internet)  
```bash
/sbin/iptables -I INPUT -w -i eth1 -m set --match-set webdeny src -j DROP  
```
