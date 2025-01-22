# Chapter 3.  Protecting Data with LUKS and NBDE 
# Topic 1 Managing Storage Device Encryption with LUKS 

## Creating Encrypted Devices at Installation

```
Creating Encrypted Devices at Installation
part /home --fstype=ext4 --size=10000 --onpart=vda2 --encrypted --passphrase=PASSPHRASE
part pv.01 --size=10000 --encrypted --passphrase=PASSPHRASE
```

## Encrypting Devices with LUKS after Installation

```
cryptsetup
cryptsetup luksFormat /dev/vdb1
cryptsetup luksDump /dev/vdb1
```

## Opening and Mounting Encrypted Devices

```
cryptsetup status /dev/vdb_hehehaw
cryptsetup close vdb1_hehehaw
```

# Topic 2 - 5
Done! (just do guided exercises, they are very good in making you understand the concepts of how to mount, use ansible roles and more)
