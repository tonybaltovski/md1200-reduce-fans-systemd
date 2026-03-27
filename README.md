# md1200-reduce-fans-systemd

A systemd service that continuously sends a fan speed command to a **Dell MD1200** disk shelf over its serial management port, keeping fan noise at a tolerable level.

## Configuration

The script accepts four positional arguments (or matching environment variables):

| Argument | Env Variable | Default | Description |
|---|---|---|---|
| `$1` | `MD1200_PORT` | `/dev/ttyS1` | Serial device path |
| `$2` | `MD1200_BAUD` | `38400` | Baud rate |
| `$3` | `MD1200_FAN_SPEED` | `10` | Target fan speed (0–100) |
| `$4` | `MD1200_SLEEP_PERIOD` | `1` | Seconds between commands |

To override values via the systemd unit, uncomment and edit the `Environment=` lines in `md1200-reduce-fans.service`.

## Install (as root)

1. Copy the script: `cp md1200-reduce-fans /usr/sbin/`
2. Copy the unit file: `cp md1200-reduce-fans.service /etc/systemd/system/`
3. Reload systemd: `systemctl daemon-reload`
4. Enable the service: `systemctl enable md1200-reduce-fans.service`
5. Start the service: `systemctl start md1200-reduce-fans.service`

## Monitoring

```bash
# Check service status
systemctl status md1200-reduce-fans.service

# Follow live logs
journalctl -fu md1200-reduce-fans.service
```
