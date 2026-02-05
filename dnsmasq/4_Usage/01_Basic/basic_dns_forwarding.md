## Summary:
This use-case demonstrates basic DNS forwarding with local overrides.
dnsmasq is configured to forward most queries to an upstream resolver
while answering selected domains locally. This shows how forwarding
policy and local decision-making can coexist ina single, simple
configuration.

## Scenario:
`dnsmasq` listens on the local host and forwards general DNS queries to
an upstream resolver. For a small set of domains, `dnsmasq` returns fixed
answers locally instead of forwarding the query.

## Why This Sequence Exists:
Real-world DNS behavior is rarely all-or-nothing. Operators often
need most queries forwarded normally while retaining control over a
small number of names. This workflow demonstrates that `dnsmasq` applies
local rules first, then falls back to forwarding when no local policy
matches.

### Start dnsmasq in the foreground:
```bash
user@host:~$ dnsmasq --no-daemon \
  --listen-address=127.0.0.1 \
  --server=1.1.1.1 \
  --address=/internal.example/192.168.1.10 \
  --log-queries
```

### Issue Queries for a Local Override:
Query a name within the overridden domain.

`dnsmasq` immediately returns the configured address without
contacting the upstream resolver. This behavior is visible in the
foreground output as a locally answered query.

### Issue Queries for a Forwarded Domain:
Query a name outside the overridden domain.

`dnsmasq` forwards the query to the upstream resolver and returns the
response to the client. This behavior is visible as a forwarded query
in the foreground output.

## Observation:
`dnsmasq` evaluates local address rules before forwarding decisions.
This ordering allows targeted overrides without disrupting normal DNS
resolution for unrelated domains.

## Cleanup:
Stop dnsmasq by interrupting the foreground process once observation
is complete.

> Notes:
> Local overrides defined with `--address` take precedence over upstream
> forwarding rules. Care should be taken to avoid unintentionally
> masking domains that should resolve externally.