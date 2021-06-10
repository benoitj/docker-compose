# firewall

setup the following rules to restrict 172.42 network to only go out to the internet

sudo iptables --insert DOCKER-USER -s 172.42.0.0/16 -d 10.1.1.0/24 -j REJECT --reject-with icmp-port-unreachable
sudo iptables --insert DOCKER-USER -s 172.42.0.0/16 -d 10.1.1.1 -j ACCEPT
sudo iptables --insert DOCKER-USER -s 172.42.0.0/16 -m state --state RELATED,ESTABLISHED -j RETURN
