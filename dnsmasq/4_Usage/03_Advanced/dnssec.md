## Summary:
The DNSSEC-related options enable dnsmasq to validate DNS responses
using cryptographic signatures. When DNSSEC is active, dnsmasq verifies
that answers from upstream resolvers are authentic and have not been
altered in transit. This transforms dnsmasq from a convenience cache
into a trust-enforcing component.

DNSSEC validation is performed transparently for clients. Clients
receive the same answers they would otherwise receive, but responses
that fail validation are rejected.

## Command Usage:
```bash
user@host:~$ dnsmasq --dnssec
```

### Explanation:
`--dnssec`
Enables DNSSEC validation for forwarded DNS queries. `dnsmasq` checks
signatures using configured trust anchors and cached key material.

`--trust-anchor=<domain>,<class>,<digest>`
specifies a DNSSEC trust anchor. This is typically used to define the
root trust anchor when not provided automatically by the system.

`--dnssec-check-unsigned`
Ensures that responses without DNSSEC signatures are accepted only
for domains that are explicitly unsigned.

## Examples:
Enable DNSSEC validation using system-provided trust anchors:
```bash
user@host:~$ dnsmasq --no-daemon \
  --dnssec --server=1.1.1.1
```
Enable DNSSEC and enforce unsigned domain checking:
```bash
user@host:~$ dnsmasq --dnssec \
  --dnssec-check-unsigned \
  --server=1.1.1.1
```

## Use Cases:
- Detect and block tampered DNS responses.
- Enforce trust boundaries for security sensitive environments.
- Improve integrity of name resolution without deploying a full
  validating resolver stack.
- Combine DNSSEC validation with local caching and policy rules.

> Notes:
> DNSSEC validation depends on accurate system time. Systems with
> incorrect clocks may experience validation failures.
> 
> Enabling DNSSEC increases CPU usage slightly due to cryptographic
> verification, but remains suitable for small and medium networks.