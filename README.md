## A minimal prerequisite:
```
USB key
Personal computer with a:
4-core processor, 
16GB of RAM, 
2 x SSD drives (128GB) and 
1 x SATA hard drive.
```
Advanced optional Google Coral TPU or GPU!
Your hardware needs to support IOMMU (I/O Memory Management Unit) interrupt remapping, this includes the CPU and the motherboard.

Generally, Intel systems with VT-d and AMD systems with AMD-Vi support this.
(read: https://docs.frigate.video/frigate/hardware/)

Example setting in BIOS: ![IMG_20230913_130115](https://github.com/Trzinka/HA-Windows-VM-on-Proxmox/assets/40424965/c83c12be-9c9a-439f-88ee-f2d638fc5770)

**********************************************************************************************************************************

First, go to the website: https://www.proxmox.com/en/downloads/proxmox-virtual-environment 
and choose 7Proxmox VE x.x ISO Installer (the current version is 8.1) 
and click download. 
Save to desktop.

**********************************************************************************************************************************

You will also need a program for writing to a USB key: https://etcher.balena.io/

**********************************************************************************************************************************

### Install proxmox!

Watch the video: https://www.youtube.com/watch?v=42gopfIrPBY

```To install Home assistant, see the video below.```

**********************************************************************************************************************************

### Install Home Assitant OS. `Preferably on a separate disk, it can be installed on the disk on which Proxmox is installed.`

To install on a Proxmox machine use this link: https://www.home-assistant.io/installation/alternative

Watch the video: https://youtu.be/Bw6O4BNhmbY

**********************************************************************************************************************************

### Instal Windows. `Preferably on a separate disk that does not have Proxmox or HAOS installed.`

Watch the video: https://youtu.be/eyNlGAzf-L4

**********************************************************************************************************************************

### Adding a physical drive to a Windows VM in Proxmox that already contains data (formatted in FAT or NTFS)!

Graphical view of the available disks of which 2 are already used (proxmox & HAOS) and 2 disks we want to add!
![Proxmox-Add disk2](https://github.com/Trzinka/HA-Windows-VM-on-Proxmox/assets/40424965/10d177ed-2116-48c7-90e0-66392bbf270f)


Click on `pev` and select `Shell` and copy  `apt install lshw` and press enter to install
![Proxmox-PEV Shell](https://github.com/Trzinka/HA-Windows-VM-on-Proxmox/assets/40424965/1ee419a0-4e55-482a-8a6e-8bb803db0d5c)

Check & `note down details` about physical disks we want to passthrough, using following command `lshw -class disk -class storage`

You should see something like this (including the other disks), which are not shown in the picture for better inspection:
![Proxmox-Disk list](https://github.com/Trzinka/HA-Windows-VM-on-Proxmox/assets/40424965/5f5a2c79-d500-4037-ad0f-74f5667f091c)
