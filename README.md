# Debian Bootstrap for FreeBSD Linuxulator

Daily debootstrap tarballs (stable, testing, and unstable) pre-configured for use 
with FreeBSD's Linuxulator, automatically generated via GitHub Actions.

## Why?

The native `debootstrap` package on FreeBSD is currently broken. This project 
sidesteps that issue by using GitHub Actions running Ubuntu to generate clean 
Debian base tarballs ready to extract into `/compat/debian`.

## Available Releases
- Debian Stable (Bookworm)
- Debian Testing (Trixie)
- Debian Unstable (Sid)

## Architectures
- amd64
- i386
- arm64
- armhf

## Quick Start on FreeBSD

```bash
# Download the latest tarball
fetch https://github.com/YOUR_USER/YOUR_REPO/releases/latest/download/debian-stable-amd64-$(date +%Y%m%d).tar.xz

# Prepare the directory
mkdir -p /compat/debian

# Extract
tar xJf debian-stable-amd64-*.tar.xz -C /compat/debian

# Mount required filesystems
mount -t proc none /compat/debian/proc
mount -t sysfs none /compat/debian/sys
mount -t devfs none /compat/debian/dev

# Chroot in
chroot /compat/debian /bin/bash
```
