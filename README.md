# BOOTABLE
Make a Bootable External Hard Drive and Install Windows 7/8
Step 1: Format the Drive
Just place the flash drive in the USB port of your computer. Open command prompt (cmd). You can do that by pressing WINKEY+R, right click on the listed file and click on “Run as administrator“.
Enter the following commands in the same order as I did here:

diskpart
list disk
select disk z (where z is the number corresponding for your USB disk. You have to replace it with the corresponding letter from your own system).
clean
create partition primary
active
format fs=fat32 quick
assign
exit

Step 2: Mount The Windows 8 ISO Image Into A Virtual Drive
If you don’t have a physical optical drive you should mount the image into a virtual drive. You can install and use PowerISO
Step 3: Make The External Hard Disk Bootable

I’m assuming that F is your drive letter with Windows 8 ISO image and G: is the location of your external hard disk (or flash drive) . Open the command prompt screen (as administrator) and type the commands:

F:
cd boot
bootsect.exe /nt60 g:

External Hard Disk Bootable


 
Also, don’t forget to triple check the target location so you don’t accidentally delete the boot sector of your hard disk

Step 4: Copy The Installer Files

After the above step, don’t close the command prompt (at least not yet). At this moment your new external hard disk or flash drive is bootable but you need to execute one more command in order to transfer the files to your new drive. You have to type the following command line:

xcopy f:\*.* g: /e /f /h

Again replace the drive letters with the ones that apply to you. Alternatively you can copy all the files in the virtual drive to the flash drive or external hard drive by using Windows Explorer, but using XCOPY ensures that system and hidden files are also copied.

Step 5: Boot Off The External Hard Drive or USB Flash Drive

To use and boot from your newly created drive on your netbook or computer, first you have to set your computer you must set it to boot through the USB flash drive. In order to do this shut down your computer, go in the CMOS setup by pressing the “DEL” or “F2″ key when the computer power on, without unplug the newly created external hard drive or USB Flash Drive from the machine. Set the device as the primary boot option, save the changes BIOS and restart. On newer computers you can boot from the device without entering into BIOS by pressing either “ESC”, “F9″ or “F11″ (different key on different manufacturers).

External Hard Drive bootable

Now you can install Windows as usual. Please be aware that if you’ve changed the boot sequence in the BIOS, remember to change it back as it was after copying the files (usually after first automatic reboot).
