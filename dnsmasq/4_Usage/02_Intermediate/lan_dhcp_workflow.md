## Summary:
This use-case demonstrates a complete DHCP workflow for a small LAN,
combining dynamic address ranges with static host assignments. The goal
is to show how `dnsmasq` manages predictable infrastructure devices while
continuing to serve a dynamic clients from a shared pool.

## Scenario:
`dnsmasq` operates as the sole DHCP server on a LAN. A defined address
range is used for general clients, while selected hosts receive fixed
addresses and names. All configuration is expressed using discrete
options or configuration fragments to maintain clarity.

### Why This Sequence Exists:
Real networks are mixed environments. Some systems require stable
identities, while others can be assigned addresses dynamically.
`dnsmasq` supports both models simultaneously without requiring separate
services or complex configuration logic.

### Start Dnsmasq in the foreground:
```bash
user@host:~$ sudo dnsmasq --no-daemon \
  --dhcp-range=192.168.1.100,192.168.1.150,24h \
  --dhcp-host=52:54:00:12:34:56,server1,192.168.1.10 \
  --dhcp-host=52:54:00:65:43:21,printer1,192.168.1.20 \
  --domain=contoso.example --log-dhcp
```

## Dynamic Client Behavior:
Clients without static mappings receive addresses from the defined
range. Lease assignments and renewals are logged as they occur, making
address allocation viible during operation.

## Static Client Behavior:
Clients with matching MAC addresses receive the same IP address and
hostname on each request. These assignments are not drawn from the
dynamic pool and do not reduce its available capacity.

## Observation:
`dnsmasq` evaluates static host mappings before allocating addresses
from the dynamic range. This ordering ensures predictable identity for
critical systems while preserving flexibility for transient clients.

## Operational Notes:
In production deployments, static host mappings are commonly stored
in a dedicated file under `/etc/dnsmasq.d/` and loaded using
`--dhcp-hostsfile`. This approach reduces configuration sprawl and
simplifies long-term maintenance.

## Cleanup:
Stop `dnsmasq` by interrupting the foreground process once observation
is complete.

> Notes:
> This workflow assumes `dnsmasq` is the only active DHCP server on the
> network segment. Multiple DHCP servers on the same LAN can result in
> unpredictable client behavior.
> 
> Foreground execution is shown for clarity. Persistent deployments
> typically transition to systemd-managed operation after validation.