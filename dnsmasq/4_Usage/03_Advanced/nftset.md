## Summary:
The `--nftset` option integrates `dnsmasq` with nftables by dynamically
adding IP addresses returned from DNS queries into nftables sets. This
allows DNS resolution to directly influence firewall and routing
policy, enabling domain-based traffic control without static IP lists.

This mechanism is reactive and stateful. As DNS answers change,
nftables sets are updated automatically to reflect current resolution
results.

## Command Usage:
```bash
user@host:~$ dnsmasq \
  --nftset=/contoso.example/inet:filter:dns_allow
```

### Explanation:
`--nftset=/<domain>[/<domain>...]/<nftset>`
For queries matching the specified domain or domains, add resolved
IP addresses to the named nftables set. The set must exist prior to
starting `dnsmasq`.

The nftset name includes the nftables family, table, nd set name in
the form:
`<family>:<table>:<set>`

### Examples:
Add resolved addresses for a domain to an nftables set:
```bash
user@host:~$ dnsmasq --no-daemon \
  --nftset=/example.com/inet:filter:dns_allow \
  --server=1.1.1.1 --log-queries
```

Apply the same nftables set to multiple domains:
```bash
user@host:~$ dnsmasq \
  --nftset=/example.com/internal.example/inet:filter:dns_allow \
  --server=1.1.1.1
```
Combine nftables tagging with normal DNS forwarding:
```bash
user@host:~$ dnsmasq \
  --nftset=/media.example/inet:filter:media_hosts \
  --server=1.1.1.1 --cache-size
```

## Use Cases:
- Implement domain-based firewall allowlists or blocklists.
- Control outbound traffic based on DNS names rather than IP ranges.
- Support dynamic services whose addresses change frequently.
- Integrate DNS resolution directly into network policy enforcement.

> Notes:
> The referenced nftables set must exist before dnsmasq starts. dnsmasq
> does not create nftables tables or sets automatically.
> 
> Entries added to nftables sets persist according to DNS cache
> lifetimes. Expired records are removed when no longer valid.
> 
> This mechanism depends on correct DNS resolution. Blocking or
> overriding domains upstream affects which addresses are inserted.