---
layout: post
title: Installing Linux on a recent laptop
subtitle: or how do I even boot ?
---


Last week, I had to install Linux on a brand new laptop. That wasn't easy, but I learned a lot.
The various Linux distro aren't very stable on the last generation of laptops. That's fair to say.

There are several issues with Nvidia Optimus. On Windows, an Intel graphic chip is used most of the time while the Nvidia card is reserved for graphic heavy applications, improving the longevity of the battery. But on Linux the Nvidia card is always running at 100%, hence a reduced autonomy. And drivers issues.

But the first step was to boot ! Indeed, with windows 10 came the new UEFI Boot option, which brings troubles for dual booting. What was needed here was to disable the fast boot option (enabling the recognition of the USB key) and maintaining shift while restarting the computer to access the UEFI usb boot screen.
While on the grub (the screen displaying the dual boot options), edit grub options (`E` for ubuntu) and add `idle=nomwait nomodset`. Without these options, the OS won't boot.

Once on the terminal, the command `lspci | grep -e VGA -e 3D` resulted in
`00:02.0 VGA compatible controller: Intel Corporation Device 191b (rev 06)`
`01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 960M] (rev a2)`
and was the confirmation that I had an Optimus laptop.

With Fedora 23, the system boots but there are issues with the missing graphic drivers. The resolution of my screen wasn't recognized. Updating the drivers requires the last version of the kernel but the last version of the kernel needs graphic drivers.

On kubuntu 15.10, basic drivers are already present and as such the resolution of my screen was recognized. When trying to install graphic drivers with `sudo apt-get update
sudo apt-get install nvidia-352 nvidia-prime nvidia-settings
sudo reboot`, the laptop became very unstable.

So after one last formatting, I reinstalled kubuntu 15.10 and permanently modified the grub in `etc\default\grub` with `idle=nomwait nomodset`. I don't have any graphic heavy application thus the setup works fine for now and the system boots without needing my intervention.


