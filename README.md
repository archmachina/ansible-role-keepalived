# ansible-role-keepalived

[![Latest](https://github.com/noveris-inf/ansible-role-keepalived/workflows/Latest/badge.svg)](https://github.com/noveris-inf/ansible-role-keepalived/actions?query=workflow%3ALatest) [![Versioned](https://github.com/noveris-inf/ansible-role-keepalived/workflows/Versioned/badge.svg)](https://github.com/noveris-inf/ansible-role-keepalived/actions?query=workflow%3AVersioned)


Example:

```
- role: keepalived
  vars:
    vrrp_instance:
      INT_TEST:
        interface: ens160
        vri: 10
        priority: 110
        addresses:
          - "192.168.1.10/24"
          - "192.168.1.11/24"
        notify_master:
          - "/sbin/route add -net 0.0.0.0/0 gw 192.168.1.254"
        notify_backup:
          - "/sbin/route add -net 0.0.0.0/0 gw 192.168.1.254"
```

Note: Keepalived may remove the default route for the interface, so the notify script is required to readd this route if the node transitions from MASTER to BACKUP.
