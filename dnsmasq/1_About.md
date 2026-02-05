## Intent:
dnsmasq is a lightweight network infrastructure service providing DNS
forwarding, caching, DHCP, and optional DNSSEC validation for small to
medium-sized networks. It is designed to combine essential name and
address services into a single daemon with minimal resource usage and
simple configuration semantics.

The tool is commonly deployed on routers, virtualization hosts, and
edge servers where authoritative DNS is unnecessary, but fast and
controllable name resolution and address assignment are required.

## Comparable Tools:
ISC dhcpd
bind
unbound
systemd-resolved
kea-dhcp

## Pros:
Combines DNS and DHCP in a single daemon.
Low memory and CPU footprint.
Supports split-horizon DNS and per-domain forwarding.
Integrates DNSSEC validation without full authoritative complexity.
Supports dynamic tagging and conditional behavior.
Well-documented in distribution wikis and upstream manuals.

## Cons:
Not intended for large-scale authoritative DNS hosting.
Configuration complexity increases significantly with advanced use.
Feature surface is broad for a single binary.
Limited separation between DNS and DHCP lifecycle management.
Advanced behavior often requires careful ordering of configuration
fragments.

## Sources:
https://thekelleys.org.uk/dnsmasq/doc.html

https://wiki.archlinux.org/title/Dnsmasq