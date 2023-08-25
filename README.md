# Automatically restart unhealthy docker containers

The systemd unit checks every 30 seconds for unhealthy docker containers and restarts them.


## Install

```sh
sudo curl -fsSL --output /etc/systemd/system/docker-autoheal.service https://raw.githubusercontent.com/ioqy/docker-autoheal-systemd/master/docker-autoheal.service
sudo systemctl daemon-reload
sudo systemctl enable --now docker-autoheal.service
```

## Uninstall

```sh
sudo systemctl disable --now docker-autoheal.service
sudo rm /etc/systemd/system/docker-autoheal.service
sudo systemctl daemon-reload
```
