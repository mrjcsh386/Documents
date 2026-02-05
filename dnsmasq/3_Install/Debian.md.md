## Install DNSMasq on Debian
Install dnsmasq on Debian using `apt`, and run it via systemd or in the
foreground for manual operation.

### Packages:
dnsmasq

### Installation steps:
```bash
user@host:~$ sudo apt update
user@host:~$ sudo apt install dnsmasq
```

### Systemd deployment:
```bash
# By default, services are started and enabled after installation
# when using Debian based flavors of Linux.
user@host:~$ sudo systemctl enable --now dnsmasq.service
```

### Manual deployment:
```bash
user@host:~$ /usr/sbin/dnsmasq --no-daemon ${sec_options} ${my_options}
```

### Sources:
Debian Wiki: https://wiki.debian.org/dnsmasq