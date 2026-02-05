## Summary:
This file describes the minimal steps required to start dnsmasq for
the first time, validate configuration syntax, and choose between
foreground execution and systemd-managed operation. The goal is to
confirm corected installation and basic DNS functionality before
enabling additional features such as DHCP or DNSSEC.

## Initial configuration Layout:
`dnsmasq` reads its primary configuration from a single file and may
additionally load configuration fragments from a directory. A
fragmented layout is recommended to reduce complexity and improve
maintainability.

### Default primary configuration file:
`/etc/dnsmasq.conf`

### Recommended configuration directory:
`/etc/dnsmasq.d/`

### Syntax Validation:
Before starting dnsmasq, configuration syntax should be verified.
This does not start the daemon or bind network ports.
```bash
user@host:~$ /usr/sbin/dnsmasq --test
dnsmasq: syntax check OK.
```

### Foreground Execution:
Foreground execution is useful for initial testing and debugging.
The daemon does not fork and logs directly to standard output.
```bash
# Ephemeral ports(above 1024) for non 'root'
# usage. This is for testing and privilege
# is not required for this phase.
user@host:~$ dnsmasq --no-daemon --port=5353
```
When running in this mode, dnsmasq will continue running until
interruped.

### Systemd-Managed Execution:
For persistent operation, dnsmasq may be managed by systemd. This
method integrates with system startup and centralized logging.
```bash
user@host:~$ sudo systemctl start dnsmasq.service
```
To enable dnsmasq at boot:
```bash
user@host:~$ sudo systemctl enable dnsmasq.service
```

### Verifying Operation:
Once running, dnsmasq should be listening on the configured address
and port. By default, it listens on UDP and TCP port 53.

Logs may be inspected using the system journal when systemd is used.
```bash
user@host:~$ sudo journalctl -u dnsmasq.service
```

> Notes:
> Forground execution is more than a debugging convenience. Running
> dnsmasq with `--no-daemon` allows an operator to directly observe DNS
> queries as they arive, are forwarded, cached, or answered locally.
> 
> Issuing test queries from another terminal while dnsmasq runs in the
> forground creates an immediate cause-and-effect loop between client
> action and daemon behavior. This makes policy decisions, cache usage,
> and forwarding logic visible without relying on indirect logging.
> 
> Common query tools may be used for this purpose, but their detailed
> usage is intentionally covered later to keep this first-run workflow
> focused on observation rather than tooling.

## Next Steps:
After confirming basic operation, configuration fragments may be
added under `/etc/dnsmasq.d/` to define DNS forwarding behavior, local
records, or DHCP services. These topics are covered in subsequent
usage files.