# Ubuntu VMs Setup

This repository contains the configuration for setting up Ubuntu VMs based on Lenovo mini PC.

## Prerequisites

Lenovo PC

Set BIOS to boot from USB for full autoinstall experience

Set static IPs with ASUS mobile app via DHCP

## Notes

Not yet tried to install

## Steps

Download Ubuntu Server

```powershell
Invoke-WebRequest -Uri "https://mirror.2degrees.nz/ubuntu-releases/24.10/ubuntu-24.10-live-server-amd64.iso" -OutFile "$ENV:HOMEPATH\Downloads\ubuntu-24.10-live-server-amd64.iso"
```

## Create Autoinstall USBs

```powershell
winget install Rufus.Rufus
```

Create bootable USB with Rufus

Copy files to USB

```sh
# Replace the existing grub.cfg on USB
# copy boot/grub/grub.cfg t o/path/to/usb/boot/grub/
# copy autoinstall.yaml to USB root
```
