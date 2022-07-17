## Deny_all  
apt install ipset  
/sbin/ipset destroy proxy  
cd /tmp && wget https://github.com/bakup/Serpentarium/raw/main/deny_all_day/ip_all_`/bin/date +%Y%m%d\` && /sbin/ipset restore -f -! /tmp/ip_all_\`/bin/date +%Y%m%d\`  
#eth1 - external interface(To Internet)  
/sbin/iptables -I INPUT -w -i eth1 -m set --match-set proxy src -j DROP  
rm /tmp/ip_all_\`/bin/date +%Y%m%d`
