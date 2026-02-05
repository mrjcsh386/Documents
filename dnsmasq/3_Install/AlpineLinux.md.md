## Install dnsmasq on Alpine Linux
Install dnsmasq on Alpine Linux using apk, and run it in the
foreground, systemd deployment is not applicable on Alpine.

### Packages:
dnsmasq

### Installation steps:
```bash
root@host:~# apk update
root@host:~# apt add dnsmasq
```

### Manual deployment:
```bash
root@host:~# dnsmasq --no-daemon ${sec_options} ${my_options}
```

### Sources:
Alpine pkg: https://pkgs.alpinelinux.org/package/edge/main/x86/dnsmasq