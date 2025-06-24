# Ubuntu VMs Setup

This repository contains the configuration for setting up Ubuntu VMs based on Lenovo mini PC.

## Prerequisites

Lenovo PC

Press F12 for boot menu on Lenovo PC.

Set static IPs with ASUS web GUI via DHCP.

## Notes

Mobile app does not allow to set the valid 192.168.1.103 outside of the router DHCP range.

Increased the DHCP range from .99 to .110.

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

## Validate Autoinstall Configuration

Reference: [Autoinstall Validation](https://canonical-subiquity.readthedocs-hosted.com/en/latest/howto/autoinstall-validation.html)

To validate the autoinstall configuration before deployment:

```bash
# Clone the subiquity repository
git clone https://github.com/canonical/subiquity.git && cd subiquity/

# Install dependencies
make install_deps

# Validate the configuration
./scripts/validate-autoinstall-user-data.py ../autoinstall.yaml

```

**Note**: The validation script may show SNAP-related errors in development environments, but if the core autoinstall validation shows "SUCCESS", your configuration is valid.
