## Install DNSMasq on Arch Linux
Install dnsmasq using Arch Linux package management, and enable it as
a systemd service when running persistently.

### Packages:
- dnsmasq

### Installation steps:
```bash
user@host:~$ sudo pacman -Syu
user@host:~$ sudo pacman -S dnsmasq
```

### Systemd Deployment:
```bash
user@host:~$ sudo systemctl enable --now dnsmasq.service
```

### Manual Deployment:
```bash
user@host:~$ dnsmasq --no-daemon ${sec_options} ${my_options}
```

### Sources:
Arch Wiki: https://wiki.archlinux.org/title/Dnsmasq
Arch pkg: https://archlinux.org/packages/extra/x86_64/dnsmasq/