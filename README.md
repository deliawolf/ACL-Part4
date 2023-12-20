# ACL Part 4

## Configure Named Access Lists
```
Branch(config)# ip access-list extended WWW-ACCESS
Branch(config-ext-nacl)# 30 permit tcp 10.1.1.0 0.0.0.255 any eq 80
Branch(config-ext-nacl)# 40 permit tcp 10.1.1.0 0.0.0.255 any eq 443

Branch(config-ext-nacl)# interface GigabitEthernet 0/0
Branch(config-if)# ip access-group WWW-ACCESS in

Branch(config-if)# do show access-lists WWW-ACCESS
Extended IP access list WWW-ACCESS
    30 permit tcp 10.1.1.0 0.0.0.255 any eq www
    40 permit tcp 10.1.1.0 0.0.0.255 any eq 443
```
In the figure, the command output shows the commands that are used to configure an extended ACL that is named WWW-ACCESS on the Branch router. The ACL permits TCP port 80 and port 443 traffic from hosts on the 10.1.1.0/24 subnet to any destination. The ACL was applied inbound to the GigabitEthernet 0/0 interface. Notice that the CLI automatically replaced the numerical port number (80) to display the www keyword instead

Note that a reload will change the sequence numbers in the ACL. The sequence numbers will be 10 and 20 instead of 5 and 10 after the reload. Use the access-list resequence command to renumber the ACL entries in an ACL without having to reload.
