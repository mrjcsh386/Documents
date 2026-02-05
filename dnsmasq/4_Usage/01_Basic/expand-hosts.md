## Summary:
The `--expand-hosts` option instructs dnsmasq to automatically append a
configured domain suffix to simple hostnames found in hosts files.
This allows short, human-friendly names to resolve as fully qualified
domain names without duplicating entries.

When used carefully, this options enables dnsmasq to act as a small,
local naming authority backed by static files.

## Comand Usage:
```bash
user@host:~$ dnsmasq --expand-hosts \
  --domain=organization.example
```

## Explanation:
`--expand-hosts`
Expands hostnames from hosts files by appending the configured 
domain. Only simple names are expanded; fully qualified names are
left unchanged.

`--domain=<domain>`
Specifies the domain suffix used when expanding hostnames. This
option is required for --xpand-hosts to have effect.

## Examples:
Expand hostnames using a documentation-safe domain:
```bash
user@host:~$ dnsmasq --expand-hosts \
  --domain=contoso.example
```
Combine with an additional hosts file:
```bash
user@host:~$ dnsmasq --expand-hosts \
  --domain=braincastle.live \
  --addn-hosts=/etc/dnsmasq.d/hosts.local
```
Test expansion in the foreground:
```bash
user@host:~$ dnsmasq --no-daemon \
  --expand-hosts \
  --domain=widgets.local
```

## Use Cases:
- Provide consistent local DNS names without managing a full zone file.
- Reduce duplication in hosts files by avoiding repeated FQDN entries.
- Support small labs or edge networks with predictable naming.
- Combine static naming with DHCP-based address assignment later.

> Notes: The `--expand-hosts` option affects only names read from
> hosts files. It does not modify names learned from DHCP leases or
> upstream DNS.