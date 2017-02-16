### #0 Setup - navigating to the larger disk on our instance
Now, since we'll be using more space this time, you want to take a look at the disks available on your instance.  
- Do this by typing `lsblk` at the terminal prompt
- This should show you that:
  - your root directory `/` has only 10G of storage
  - there's a second disk in this instance `/mnt` which has 420G of storage
- Let's make ourselves a folder under the larger `/mnt/` directory to work out of so we don't run out of space!
  - The `sudo` command below just means "super user" and is used to over-ride the protected permissions of this root folder
  
```
sudo mkdir --mode a+rwx /mnt/workshop
cd /mnt/workshop
```
**Important Note** 
- This /mnt drive is what's called "ephemeral storage" it will disappear if you stop your instance
- This is different from your home directory on the instance, which will be kept if your **stop** your instance
  - However, if you **terminate** your instance, this home directory will *also* disappear.

