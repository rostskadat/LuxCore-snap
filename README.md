# LuxCore-snap: a snap package for LuxCore

[![luxcore](https://snapcraft.io/luxcore/badge.svg)](https://snapcraft.io/luxcore)

[![Get it from the Snap Store](https://snapcraft.io/static/images/badges/en/snap-store-black.svg)](https://snapcraft.io/luxcore)

## About LuxCore

LuxCoreRender is a physically based and unbiased rendering engine. Based on state of the art algorithms, LuxCoreRender simulates the flow of light according to physical equations, thus producing realistic images of photographic quality.

Visit the upstream project: [https://luxcorerender.org/](https://luxcorerender.org/) and [https://github.com/LuxCoreRender/LuxCore](https://github.com/LuxCoreRender/LuxCore)

## Channels

There are three maintained channels for this snap:

- `stable` contains the latest upstream release, i.e. the most recent tagged commit. **Use this if you don't know what you're doing.**
- `edge` contains automated (daily) builds from the latest master commit. **Use this to test new features. Might be unstable.**
- `beta` contains automated weekly promotions from `edge`. **Use this if you want edge with fewer updates.**

## Apps/Commands

There are multiple apps/commands included in the snap:

- `luxcore`: Run luxcoreconsole
- `luxcore.luxcoreconsole`: Run luxcoreconsole
- `luxcore.luxcoreui`: Run luxcoreui

## Troubleshooting

### Docker and LXD

If your image can not connect to internet and you have docker installed, it might be that Docker has a FW rule that drops packet. Execute the following command to fix the `DOCKER_USER` rule

```shell
sudo iptables -I DOCKER-USER -i lxdbr0 -j ACCEPT
sudo iptables -I DOCKER-USER -o lxdbr0 -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
```

### Reducing the snap size

1. get a sense of what is big inside the installed snap:

```shell
ncdu /snap/luxcore/current
```

1. Find packages that can be removed from the `stage-packages` of the main part.
1. Use an extension (`snapcraft list-extensions`) and also remove duplicated packages
