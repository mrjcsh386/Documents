## Filesystem Permissions:
Read access:
/etc/dnsmasq.conf
/etc/dnsmasq.d/
/etc/hosts
/etc/resolv.conf

### Write access:
DHCP lease file path
Default: /var/lib/misc/dnsmasq.leases
PID file path
Default: /var/run/dnsmasq.pid
Log file path when file-based logging is configured.

## User and Group Requirements:
Startup requires root privileges to bind to low-numbered ports and
configure network interfaces.

Runtime privileges may be dropped using:
--user
--group

Default runtime user: nobody
Default runtime group: dip

## Kernel and Network Capabilities:
Requires permission to bind to UDP and TCP port 53 for DNS.
Requires permission to bind to UDP ports 67 and 68 for DHCP.
Requires access to network interfaces for packet inspection.

## Security Frameworks:
### SELinux:
Requires allowance for DNS and DHCP socket binding and lease file
writes.

### AppArmor:
Requires access to configuration files, lease files, and network
sockets.

> Caution:
> Running dnsmasq without privilege dropping increases attack surface
> and is not recommended for long-lived deployments.