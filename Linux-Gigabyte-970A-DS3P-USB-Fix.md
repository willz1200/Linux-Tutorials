How to Fix the Gigabyte 970A-DS3P Motherboards USB Host Controller Under Linux Mint
===================================================================================

Linux mint doesn't seem to natively support the USB host controller on the Gigabyte 970A-DS3P motherboard. :-( Make sure to try a keyboard in every USB port when installing Linux mint. I managed to find one port that worked, all the other USB ports didn't work. If you can't find a USB port that works a PS/2 keyboard or USB to PS/2 adapter might do the trick.

Do the following to fix the USB ports on the motherboard.

1. Open the grub configuration file
```
sudo nano /etc/default/grub
```

2. Find the following lines in the file
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

3. Change them to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash iommu=soft"
GRUB_CMDLINE_LINUX="iommu=soft"
```

4. Run the following command to update the grub configuration
```
sudo update-grub
```

5. Reboot your computer, all USB ports should now be working :-)
