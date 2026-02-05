## Install dnsmasq on CentOS
Install dnsmasq on CentOS Stream using `dnf`, and run it under systemd
or in the foreground for manual operation.

### Packages:
dnsmasq

### Installation steps:
```bash
user@host:~$ sudo dnf install -y dnsmasq
```

### Systemd deployment:
```bash
user@host:~$ systemctl enable --now dnsmasq.service
```

### Manual deployment:
```bash
user@host:~$ dnsmasq --no-daemon ${sec_options} ${my_options}
```