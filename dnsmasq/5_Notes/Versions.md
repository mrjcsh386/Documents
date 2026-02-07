## Summary:
This file lists notable dnsmasq releases that introduced meaningful
changes in behavior, security, or scope. The intent is to provide
historical context rather than a complete changelog.

## Versions:
### 2.40
Introduced early DNSSEC-related groundwork and expanded DHCP feature
coverage. This marked dnsmasq's transition from a simple forwarder
into a policy-aware network service.

### 2.60
Improved DHCPv6 support and expanded tagging capabilities, allowing
more conditional behavior based on client attributes.

### 2.70
Added enhanced security features, including improved rebinding
protection and stricter DNS behavior defaults.

### 2.76
Introduced support for ipset integration, enabling DNS-driven
firewall policy for Linux systems.

### 2.80
Expanded DNSSEC validation support and improved performance for
signed zones, making dnsmasq viable as a lightweight validating
resolver.

### 2.85
Added nftables set integration, replacing or complementing ipset in
modern Linux environments and aligning dnsmasq with contemporary
firewall tooling.

### 2.90
Continued refinement of DNSSEC behavior, cache handling, and
security-related defaults. Improved robustness for long-running
deployments.

> Notes:
> dnsmasq follows a rapid but conservative release model. Features are
> often introduced incrementally and hardened across several versions.
> 
> Distribution packages may backport features or fixes without changing
> the reported version number. Behavior should be verified against the
> packaged build when precision matters.