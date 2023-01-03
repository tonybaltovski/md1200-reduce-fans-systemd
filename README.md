# md1200-reduce-fans-systemd

## Install (as root)
1. Copy `md1200-reduce-fans` to `/usr/sbin/` using `cp md1200-reduce-fans /usr/sbin/`
2. Copy `md1200-reduce-fans.service` to `/etc/systemd/system/` using `cp md1200-reduce-fans.service /etc/systemd/system/`
3. Reload the Systemd manager using `systemctl daemon-reload`
4. Enable the service using `systemctl enable md1200-reduce-fans.service`
5. Start the service using `systemctl start md1200-reduce-fans.service`
