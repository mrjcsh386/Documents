## Required Dependencies:
libc
Minimum version: glibc 2.17 or equivalent
Purpose: Core runtime support.

libidn2
Minimum version: 2.0
Purpose: Internationalized domain name handling.

### Recommended Dependencies:
libnettle
Minimum version: 3.4
Enables: DNSSEC cryptographic validation.

libgmp
Minimum version: 6.1
Enables: Improved performance for DNSSEC signature verification.

### Optional Dependencies:
libdbus
Purpose: Enables DBus control interface when enabled at build time.

liblua
Purpose: Enables Lua scripting for DHCP lease events.

> Notes:
> DNSSEC support is compiled in by most modern distributions but may
> require explicit library availability at build time.