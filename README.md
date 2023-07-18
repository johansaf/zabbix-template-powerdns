# Zabbix Template: PowerDNS

Based on [mkhon/zabbix-powerdns](https://github.com/mkhon/zabbix-powerdns/tree/master).

Tested with Zabbix 6.0.12 and PowerDNS 4.8.1.

## Installation

Add something like this to your sudoers file:
```
zabbix  ALL=(ALL) NOPASSWD: /usr/bin/pdns_control list
```

The template uses the zabbix agent on the server for fetching values. Add this user parameter to your zabbix-agent config. For zabbix-agent2 on Ubuntu it's in `/etc/zabbix/zabbix_agent2.d/plugins.d`:
```
$ cat powerdns.conf
UserParameter=powerdns.stats,sudo pdns_control list
```

Add the template to your host and Zabbix should start fetching data. If there's issues try to change the "Active Check" for the raw data to a passive check instead.
