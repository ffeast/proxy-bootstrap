
# proxy-bootstrap

This is an ansible playbook to quickly bring up a network of private proxy servers spread across multipe hosting providers

## Architecture
TBD
### Technical details
 - `centos6` is used as an operating system
 - [3proxy](https://github.com/z3APA3A/3proxy) is used as a socks/http proxy server
 - playbook tested with `ansible 2.5.1`

## Production usage
This playbook has been used for a while for distributed crawling


## Bootstrap
 1. Purchase the cheapest KVM hosting from any provider with 1 main + N extra IPs. This step needs to be repeated as many times as possible. Choose `linux/centos6` as the operating system to use
 2. Prepare servers that would host services using the proxies (also `centos6`)
 3. Add your ssh pubkey to `/root/.ssh/authorized_keys` for all of the proxy servers and services  (automation is possible depending on your hosting provider)
 4. Put the hostnames and IP addresses into `ansible_inventory`
 5. `ansible-playbook -i ansible_inventory ansible_playbook.yml`
 6. You're done!


## Monitoring
So far only manual zabbix configuration is possible, although it shouldn't be a problem given you have all zabbix agents configured and know how to use zabbix templates
