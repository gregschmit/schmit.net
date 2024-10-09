# Hyperion

My personal SSH, postgres, network, and file server.

## Security

Always check the following after fresh install or dist upgrade:
- Ensure `PasswordAuthentication no` is set in `/etc/ssh/sshd_config`.
- Ensure `/etc/nftables.conf` is set from `conf/nftables.conf`.
- Ensure postgres user passwords for users `postgres` and `root` are set appropriately.
