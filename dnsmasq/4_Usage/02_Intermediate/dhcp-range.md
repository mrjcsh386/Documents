## Summary:
The `--dhcp-range` options enables `dnsmasq`'s DHCP server and defines the
pool of addresses available for dynamic assignment. This command marks
the transition from dnsmasq acting as a passive DNS helper to an active
network authority.

One enabled, dnsmasq begins managing address leases, tracking client
state, and coordinating DHCP behavior with DNS when configured.

## Command Usage:
```bash
user@host:~$ sudo dnsmasq \
  --dhcp-range=192.168.1.100,192.168.1.150,12h
```

### Explanation:
`--dhcp-range=<start>,<end>[,<lease>]`
Enables DHCP and specifies the inclusive address range dnsmasq may
assign to clients. An optional lease duration may be provided.

Lease duration may be expressed in minutes, hours, or days.

## Examples:
Enable DHCP with a 12-hour lease duration:
```bash
user@host:~$ sudo dnsmasq --no-daemon \
  --dhcp-range=192.168.1.100,192.168.1.150,12h
```
Enable DHCP with a default lease duration:
```bash
user@host:~$ sudo dnsmasq \
  --dhcp-range=192.168.1.100,192.168.1.150
```
Combine DHCP with a fixed domain for client names sharing network with eth1:
```bash
user@host:~$ sudo dnsmasq --interface=eth1 \
  --domain=contoso.local \
  --dhcp-range=192.168.1.100,192.168.1.150,12h
```

## Use Cases:
- Provide dynamic IP addresses to a small LAN.
- Replace consumer router DHCP services with explicit configuration.
- Prepare for static mapings and DNS integration.
- Centralized address management on a gateway or edge host.

> Notes:
> Enabling `--dhcp-range` implicitly enables the DHCP server. Care should
> be taken to ensure no other DHCP server is active on the same network.
> 
> DHCP operation typically requires dnsmasq to run with elevated
> privileges and to bind to the appropriate network interface
> (`--interface=<iface>`).