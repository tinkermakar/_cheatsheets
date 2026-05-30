# Virtualization Cheatsheet

1. in QEMU/kvm bridge networks -- if `bridge` is unavailable use `open` networks

1. On PiKVM/Raspberry Pi, enable Avahi/mDNS to make possible accessing it via a custom `.local` URL:
    ```bash
    sudo systemctl enable --now avahi-daemon
    ```
