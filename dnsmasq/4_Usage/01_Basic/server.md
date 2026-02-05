## Summary:
The `--server` option defines upstream DNS servers which dnsmasq will
forward queries to. It may be used as a general upstream resolver
setting, or as a per-domain forwarding rule to send specific domains
to specific upstream servers.

This option is a core building block for split DNS, where internal
domains resolve via internal resolvers and all other names resolve via
public resolvers.

## Command Usage:
```bash
user@host:~$ dnsmasq --server=1.1.1.1
```

## Explanation:
`--server=/<domain>/<ipaddr>`
For queries in <domain>, forward requests to <ipaddr>.

`--server=<ipaddr>`
For all other queries, forward requests to <ipaddr>.

## Examples:
Use a single upstream resolver for all queries:
```bash
user@host:~$ dnsmasq --server=1.1.1.1
```
Forward a specific internal domain to an internal resolver
```bash
user@host:~$ dnsmasq \
  --server=/oranization.example/192.168.1.53
```
Combine per-domain forwarding with a general upstream resolver:
```bash
user@host:~$ dnsmasq \
  --server=/organization.example/192.168.1.53 \
  --server=1.1.1.1
```
Run in the foreground for quick testing:
```bash
user@host:~$ dnsmasq --no-daemon \
  --server=/organization.example/192.168.1.53 \
  --server=1.1.1.1
```

## Use Cases:
- Forward all DNS queries to a chosen upstream resolver.
- Implement split DNS for internal versus public namespaces.
- Route reverse or special domains to dedicated upstream servers.
- Reduce latency by placing a local caching forwarder near clients.

> Notes: Per-domain forwarding only matches queries within the
> specified domain. It does not convert dnsmasq into an
> authoritative server.