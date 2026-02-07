## Summary:
the `--dhcp-host` option defines static DHCP mappings for specific
clients. It allows an operator to assign predictable IP addresses and
hostnames based on client identifiers such as MAC addresses. This
creates stable network identities while retaining centralized DHCP
management.

Static mapings integrate naturally with DNS, enabling consistent
name resolution for known hosts.

## Command Usage:
```bash
user@host:~$ sudo dnsmasq \
  --dhcp-host=52:54:00:12:34:56,192.168.1.20
```

### Explanation:
`--dhcp-host=<hostspec>,<reservation>`
Specifies a static mapping for a DHCP client. The host specification
may include a MAC address, hostname, IP address, and optional tags.
Fields are separated by commas.

## Examples:
Assign a fixed IP address to a client by MAC address:
```bash
user@host:~$ sudo dnsmasq --no-daemon \
  --dhc-host=52:54:00:12:34:56,192.168.1.20
```
Read static host mappings from a file:
```bash
user@host:~$ sudo dnsmasq \
  --dhcp-hostsfile=/etc/dnsmasq.d/dhcp.hosts
```

**Example hosts file entry format:**
```/etc/dnsmasq.d/dhcp.hosts
# Workstation reservation mapping
52:54:00:12:34:56,workstation,192.168.1.20
```

## Use Cases:
- Ensure critical systems always receive the same IP address.
- Provide stable DNS names for servers and infrastructure devices.
- Simplify firewall and routing rules by relying on predicable
  addressing.
- Combine dynamic pools with reserved addresses cleanly.

> Notes:
> Static DHCP assignments defined with `--dhcp-host` take precedence over
> dynamic ranges defined with `--dhcp-range`.
> 
> When a hostname is provided, dnsmassq may register the name in DNS
> depending on domain and DHCP-related settings.