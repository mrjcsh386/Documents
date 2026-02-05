## Summary:
The `--liste-address` option restricts dnsmasq to listening only on
specific local IP addresses. This allows precise control over which
interfaces and networks may send DNS queries to the daemon. Using this
option avoids unintended exposure on all interfaces, especialy on
multi-homed systems.

When one or more listen addresses are defined, dnsmasq will ignore
other local addresses unless explicitly included.

## Command Usage:
```bash
user@host:~$ dnsmasq --listen-address=127.0.0.1
```

## Explanation:
`--listen-address=<ipaddr`
Specifies one or more local IP addresses on which dnsmasq will
accept DNS queries. The option may be repeated to liston on multiple
addresses.

## Examples:
Listen only on the loopback interface:
```bash
user@host:~$ dnsmasq --listen-address=127.0.0.1
```
Listen on both loopback and a LAN address:
```bash
user@host:~$ dnsmasq \
  --listen-address=127.0.0.1 \
  --listen-address=192.168.1.53
```
Combine with foreground execution for testing:
```bash
user@host:~$ dnsmasq --no-daemon \
  --listen-address=127.0.0.1
```

## Use Cases:
- Restrict DNS service to the local host for caching purposes.
- Bind dnsmasq to a specific LAN interface on a gateway or router.
- Prevent dnsmasq from listening on unintended or public interfaces.
- Support split-horizon DNS when combined with interface-based options.

> Notes: if `--listen-address` is not specified, dnsmasq listens on
>  all available interfaces by default, subject to other interface-related
>  options.