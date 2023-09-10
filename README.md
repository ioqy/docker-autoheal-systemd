# Automatically restart unhealthy docker containers

The systemd unit checks every 30 seconds for unhealthy docker containers and restarts them.

Based on the idea of to https://github.com/willfarrell/docker-autoheal. But simpler and with less features.

## Changing the monitoring interval

Edit the file `/etc/systemd/system/docker-autoheal.service` and change the value of the environment variable `AUTOHEAL_INTERVAL`.

## Install

```sh
sudo wget --quiet --output-document /etc/systemd/system/docker-autoheal.service https://raw.githubusercontent.com/ioqy/docker-autoheal-systemd/master/docker-autoheal.service
sudo systemctl daemon-reload
sudo systemctl enable --now docker-autoheal.service
```

## Uninstall

```sh
sudo systemctl disable --now docker-autoheal.service
sudo rm /etc/systemd/system/docker-autoheal.service
sudo systemctl daemon-reload
```
