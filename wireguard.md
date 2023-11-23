### Install and configure client
##### Ubuntu CLI
```
### install
sudo apt install wireguard
### add connection
nmcli connection import type wireguard file ~/Downloads/vpn.conf
### disable autoconnect
nmcli connection modify vpn autoconnect no
### disconnect
nmcli connection down vpn
### connect
nmcli connection up vpn
### delete connection
nmcli connection delete vpn
### show all connection
nmcli connection show
```
##### Ubuntu GUI
https://github.com/UnnoTed/wireguird

##### Other OS
https://www.wireguard.com/install/

### Debug
##### Get logs
```
## enable wireguard kernel module
echo "module wireguard +p" | sudo tee /sys/kernel/debug/dynamic_debug/control
## tail kernel logs
dmesg -wT
## disable wireguard kernel module
echo "module wireguard -p" | sudo tee /sys/kernel/debug/dynamic_debug/control
```
##### Wrong rules
```
sudo wg-quick down wg0
## del all iptable rules in /etc/wireguard/wg0.conf
sudo systemctl start wg-quick@wg0
```

### new vpn client
add client conf in **roles/wireguard/templates** and set unique IP address

add Peer in **roles/wireguard/templates/wg0.conf.j2** and set unique IP address

add tasks in **roles/wireguard/tasks/wireguard.yaml**

In **site.yml** add new user vars in role **wireguard** 