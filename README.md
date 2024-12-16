# Hyperion

My personal SSH, postgres, network, and file server.

## Security

Always check the following after fresh install or dist upgrade:
- Ensure `PasswordAuthentication no` is set in `/etc/ssh/sshd_config`.
- Ensure `/etc/nftables.conf` is set from `conf/nftables.conf`.
- Ensure postgres user passwords for users `postgres` and `root` are set appropriately.

## OpenRGB Config on Physical Servers:

```sh
root@big-red:~# cat /etc/systemd/system/openrgb.service
[Service]
Type=oneshot
ExecStart=/usr/bin/openrgb -c ff0000 -m Direct

[Install]
WantedBy=multi-user.target
```
