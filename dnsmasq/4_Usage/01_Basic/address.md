## Summary:
The `--address` option forces dnsmasq to return a fixed IP address for
all queries within one or more specified domains. This allows domains
to be redirected, sinkholed, or locally terminated without consulting
upstream DNS servers.

This option is commonly used for simple policy enforcement, service
redirection, or local overrides where authoritative DNS is unnecessary.

## Command Usage:
```bash
user@host:~$ dnsmasq \
  --address=/organization.example/127.0.0.1
```

## Explanation:
`--address=/<domain>/<ipaddr>`
For any DNS query ending in `<domain>` return `<ipaddr>` as the answer.
The query is not forwarded to upstream servers.

The option may be repeated to define multiple domain-to-address
mappings.

## Examples:
Redirect all queries for a domain to the local host:
```bash
user@host:~$ dnsmasq --no-daemon \
  --address=/example.com/127.0.0.1
```
Redirect multiple domains to the same address:
```bash
user@host:~$ dnsmasq \
  --address=/ads.example/0.0.0.0 \
  --address=/tracking.example/0.0.0.0
```
Combine domain redirection with normal upstream resolution:
```bash
user@host:~$ dnsmasq \
  --address=/internal.example/192.168.1.10 \
  --server=1.1.1.1
```

## Use Cases:
- Redirect traffic for a domain to a local service.
- Block access to unwanted domains by returning a non-routable address.
- Override external DNS answers for internal testing or development.
- Implement simple policy rules without running an authoritative server.

> Notes:
> The `--address` options applies only to DNS answers generated locally by
> dnsmasq. It does not modify upstream data or cache behavior for other
> domains.