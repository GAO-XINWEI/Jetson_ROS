# Backup and Install the Jeston Nano System

## Backup

To create a backup of your Jetson Nano SD card using your Ubuntu computer, you can create an image of the SD card. Here's a step-by-step guide to doing that:

1. Insert the SD card into your Ubuntu computer using an SD card reader.

2. Open a terminal by pressing Ctrl + Alt + T.

3. Find the device name of the SD card by running the following command:
```bash
sudo fdisk -l
```

4. Unmount all partitions of the SD card by running the following command (replace '/dev/mmcblk0' with the correct device name):
```bash
sudo umount /dev/mmcblk0*
```

5. Create a compressed image file of the SD card using the following command (replace '/dev/mmcblk0' with the correct device name, and 'JetsonBackup.img' with your desired file name):
```bash
sudo dd if=/dev/mmcblk0 bs=4M status=progress | gzip > ~/Documents/JetsonBackup.img.gz
# or
sudo dd if=/dev/mmcblk0 bs=4M status=progress | gzip > ~/JetsonBackup.img.gz
```
This command will create a compressed image file called 'backup.img.gz' in your home directory. The process might take some time, depending on the size of the SD card. Once the process is complete, you'll have a compressed backup image of your Jetson Nano SD card. You can now safely remove the SD card from your Ubuntu computer.


## Install

To restore the system from the compressed backup image in the future:

1. Insert a new SD card into your Ubuntu computer.

2. Find the device name of the new SD card using the sudo fdisk -l command.
```bash
sudo dd if=/dev/zero of=/dev/mmcblk0* bs=4M count=10 status=progress
```

3. Unmount all partitions of the new SD card using:
```bash
sudo umount /dev/mmcblk0*
```

5. Write the compressed backup image to the new SD card using the following command (replace 'sdX' with the correct device name, and 'JetsonBackup.img.gz' with your compressed image file name):
```bash
gzip -dc ~/Documents/JetsonBackup.img.gz | sudo dd of=/dev/mmcblk0 bs=4M status=progress
# or
gzip -dc ~/JetsonBackup.img.gz | sudo dd of=/dev/mmcblk0 bs=4M status=progress
```
Once the process is complete, you can insert the new SD card into your Jetson Nano, and it should boot up with the backed-up system.
