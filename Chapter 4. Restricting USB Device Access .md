# Chapter 4. Restricting USB Device Access
# Topic 1 Controlling USB Access with USBGuard
## What you will learn ?
Configure and use USBGuard to selectively control USB device access

## Introduction to USBGuard
USBGuard is a software that protects your system from rouge USB devices by implementing basic allowlist and blocklist based on device.

## Commands

```
dnf install usbguard
systemctl enable --now usbguard.service
cat /etc/usbguard/rules.conf
dnf install usbutils udisks2
```

More commands are discussed in detail, do the next lab execrise to get a better understanding of everything.

# Topic 2 Guided Exercise: Controlling USB access with USBGuard
Done!

# Topic 3 End of chanpter Lab
Done!
