## Summary:
This use-case demonstrates dnsmasq as a local DNS caching
resolver for a single host. The goal is to observe how repeated queries
are handled differently once answers are cached, using foreground
execution and query logging to make behavior visible.

## Scenario:
dnsmasq is started in the foreground and bound only to the loopback
address. A fixed upstream resolver is defined. A client then issues the
same DNS query multiple times, allowing the operator observe the
transition from upstreamm resolution to cached responses.

### Why This Sequence Exists:
DNS caching is temporal behavior. The first query establishes state,
and subsequent queries reveal how that state is reused. Running in the
foreground with query logging exposes this casue-and-effect loop
without relying on external tools or service logs.

Start dnsmasq in the foreground:
```bash
user@host:~$ dnsmasq --no-daemon \
  --listen-address=127.0.0.1 \
  --server=1.1.1.1 \
  --port=5353 \
  --cache-size=150 \
  --log-queries
```

### Issue a Test Query (first request):
From another terminal on the same host, issue a DNS query using any
available resolver tool configured to use `127.0.0.1`.

The first query is forwarded upstream and stored in the cache. This
is visible in the foreground output as forwarded query.

### Issue the Same Query Again:
Repeat the same query after a short delay.

The second query is answered directly from the cace. The foreground
output reflects a local cache response rather than an upstream
forward.

## Observation:
The difference between the first and second query is not the answer,
but the path taken to produce it. dnsmasq reduces latency and upstream
dependency by reusing cached results until their time-to-live expires.

## Cleanup:
Stop dnsmasq by interrupting the foreground process once observation
is complete

> Notes:
> This workflow emphasizes observation over tooling. Any DNS client
> capable of querying a local resolver is sufficient. The specific
> client commands are intentionaly deferred to keep focus on daemon
> behavior rather than query syntax.
> 
> Cache behavior is affected by time-to-live values provided by
> upstream servers and by local cache size limits.