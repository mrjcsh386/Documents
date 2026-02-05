## CPU:
No special CPU instruction set support is required. dnsmasq operates
on standard x86_64, ARMv7, ARMv8, and comparable architectures.

## CPU Class and Speed:
Minimum: Any general-purpose CPU capable of sustaining basic network
I/O.
Recommended: 1 GHz or higher for networks with moderate DHCP churn or
high DNS query volume.

## RAM:
Minimum: 16 MB
Recommended: 64 MB or more when DNS caching, DHCP, and DNSSEC
validation are enabled simultaneously.

## Disk:
Minimum: 5 MB for binaries and base configuration.
Recommended: 20 MB or more to accommodate lease files, logs, and
configuration fragments.

## Firmware:
No BIOS or UEFI requirements beyond those necessary to boot the host
operating system.