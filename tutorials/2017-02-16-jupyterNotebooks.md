# Introduction to Jupyter (ipython) Notebooks

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

### #1 Launching the notebook server
We'll be working on this tutorial for a while and, as you noticed last time, sometimes the the wifi cuts out and interrupts your `ssh` connection. **WHAT TO DOOOO???** 
```
screen
ipython notebook
```
Now that you've launched the notebook from your instance, you can navigate to the Jupyter notebook server using your regular internet browser window!
You just need to know your instance's public DNS address and the port you set up under the security rules (8888)

`http://ec2-204-236-222-237.compute-1.amazonaws.com:8888`

