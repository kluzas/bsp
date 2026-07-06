# INTRO

It is a fork repo of `bsp - Radxa BSP Build Tool`

I made changes so I could build u-boot image for radxa CM3. This module is used on [Sipeed NanoCluster](https://wiki.sipeed.com/hardware/en/cluster/NanoCluster/index.html)


## Instalation

```
rkdeveloptool ld
rkdeveloptool db rkboot.bin 
rkdeveloptool wl 64 idbloader.img 
rkdeveloptool wl 16384 u-boot.itb 
rkdeveloptool rd
```