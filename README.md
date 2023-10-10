# Automatically restart unhealthy docker containers

The systemd unit checks every 30 seconds for unhealthy docker containers and restarts them.

Based on the idea of to https://github.com/willfarrell/docker-autoheal. But simpler and with less features.

## Changing the monitoring interval

Create the file `/etc/docker-autoheal.env` and add a line with `autoheal_interval_seconds=30`, where `30` is the number of seconds you want as an interval.

Afterwards restart the service with the command `systemctl restart docker-autoheal.service`.

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
