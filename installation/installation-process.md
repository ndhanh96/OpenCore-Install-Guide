# Quy trình cài đặt

Now that you've finished setting up OpenCore, you're finally able to boot, main things to keep in mind:
Những điều nên nhớ khi đã cài đặt xong Opencore và boot được: 

* Cài đặt BIOS để tối ưu cho MacOS
* Read up on the [Multiboot Guide](https://hackintosh-multiboot.gitbook.io/hackintosh-multiboot/)
  * Mainly relevant for those running a single drive for multiple OSes
* And a copy of the [General Troubleshooting](../troubleshooting/troubleshooting.md) page
* Read up on the [macOS Boot Process](../troubleshooting/boot.md)
  * Can help first time installers better understand where they may be getting stuck
* And a ton of patience

## Kiểm tra lại 1 lần nữa

One last thing we should go over before booting is how your EFI is setup:
Chúng ta nên kiểm tra lại EFI trước khi boot:

Good EFI          |  Bad EFI
:-------------------------:|:-------------------------:
![](../images/installation/install-md/good-efi.png)  |  ![](../images/installation/install-md/bad-efi.png)
Có thư mục EFI trên phân vùng EFI | Không có thư mục EFI
Những file APCI đã được biên dịch(.aml) | File APCI chưa được biên dịch(.dsl)
Không có DSDT |* Có DSDT
Xoá Drivers(.efi) không cần thiết | Để như mặc định
Xoá Tools(.efi) không cần thiết | Để như mặc định
Tất cả cái file trong thư mục kext có đuôi .kext | Có nhiều thư mục không liên quan
File config.plist phải ở trong EFI/OC | Tên và vị trí của .plist đều sai
Chỉ cần dùng những kext cần thiết | Tải về tất cả các kext được nêu ra.

And a reminder that slowgeek site is your friend:

* [**Sanity Checker**](https://opencore.slowgeek.com)

## Booting the OpenCore USB

So you're now ready to finally put the USB stick into your computer and boot off of it, remember that your laptop will still default to the internal drive with Windows so you'll need to enter the BIOS or boot menu and select the USB. You'll need to check in the user manual or use a bit of google to find out what Fn key accesses the BIOS and boot menu(ie. Esc, F2, F10 or F12)

Once you boot the USB, you'll likely be greeted to the following boot options:

1. Windows
2. macOS Base System (External) / Install macOS Catalina (External)
3. OpenShell.efi
4. Reset NVRAM

For use, **Option 2.** is the one we want. Depending how the installer was made, it may report as either **"macOS Base System (External)"** if created in Linux or Windows and **"Install macOS Catalina (External)"** if created in macOS.

## macOS Installer

So you've finally got the installer booted, got through the verbose and hit the installer! Now that you've gotten this far,  the main things to keep in mind:

* Drives you wish to install macOS on **must** be both of GUID partition Scheme **and** APFS
  * High Sierra on HDD and all Sierra users will need to use macOS Journaled(HFS+)
* The drive **must** also have a 200MB partition
  * By default, macOS will setup freshly formatted drives with 200MB
  * See the [Multiboot Guide](https://hackintosh-multiboot.gitbook.io/hackintosh-multiboot/) for more info on partitioning a Windows Drive

Once you start the installation, you will want to wait until the system restarts. You will once again want to boot into OpenCore, but rather than selecting your USB installer/recovery - you will want to select the macOS installer on the hard drive to continue installation. You should get an apple logo, and after a few minutes you should get a timer at the bottom saying "x minutes remaining". This may be a good time to get a drink or snack as this will take a while. It may restart a couple more times, but if all goes well, it should finally plop you at the "Setup your Mac screen"

You're in! 🎉
You will want to go through the Post-Installation pages to finish setting up your system.
