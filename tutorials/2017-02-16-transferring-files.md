# Transferring files
Authored by Lizzy Wilbanks for Swarthmore College BIOL133, Spring 2017
using material adapted from a tutorial in EDAMAME: Explorations in Data Analysis for Metagenomic Advances in Microbial Ecology 2015
[EDAMAME-2015 EC2-files tutorial](https://github.com/edamame-course/2015-tutorials/blob/master/final/2015-06-22-EC2_Connection_FileTransfer.md)

This section of the tutorial will teach or remind you HOW TO:
- Transfer files between your AWS EC2 instance and your laptop using `scp`
- Download publicly-hosted data to an EC2 instance using `wget`  

###0.  Where am I?  
Sometimes, all the terminal screens sort of look the same. When you're copying files back and forth, it's important know which machine you're talking to:  your own laptop, or your EC2 instance in the cloud?

- Keep your terminal window open where you have `ssh` into the EC2 machine. 
- Now, start another, new terminal window.  
 - **NOTE** This new window is *NOT* connected to the EC2.  Instead it's just your regular ole laptop
- Verify that your these windows are connected to different machines examining the home directory in both your `ssh` and new terminal

``` 
pwd
```
See how they're different? One you've connected to EC2 (ubuntu), the other is just your local machine (whatever your user name is)

You can also look at the address of the machine using the command (Windows users, did this work?)
```
hostname
```

###1. Using `scp` to transfer files between your machine and your EC2 instance

Next we will go over how to copy a file from your personal computer to your EC2 instance using `scp`. The usage is very similar to `ssh`.  

Download the following file onto your laptop's Desktop by clicking [this link] (https://www.dropbox.com/s/9y41he4ol62gu0b/cloud.txt?dl=0)

Now we're going to copy this file you downloaded from your laptop onto the remote EC2 machine.  

Find your terminal window that's just your local machine (see above) and run the appropriate version 
of the command below.  
*NOTE* you have to adapt this command to give it the right paths and DNS info!
```
scp -i **/path/to/your/keyfile.pem** **path/to/the/file/you/want/to/copy** ubuntu@"your public DNS":**/path/where/to /copy/the/file**
```
How do you know where you want to put the file?  
- Look first at the directory structure on your EC2 machine
- Type `pwd` once you've navigatated where you want to put this file!
- put that path after the colon in the example above

An example from my file structure and EC2 instance!
```
scp -i /Users/ewilbanks/Desktop/amazon.pem /Users/ewilbanks/Desktop/cloud.txt ubuntu@ec2-52-5-171-50.compute-1.amazonaws.com:/home/ubuntu/
```

Now look on your EC2 machine and use `nano` to open the file.
Make some changes to this file by adding some text.

Now we'll copy this modified file back to your laptop:
- use the terminal window that is connected to your local machine
- We'll use a similar command to that above, but just switch the second and third arguments
```
scp -i "path to your keyfile.pem" ubuntu@"your public DNS":"path to the file you want to copy" "path where to save the file on your computer"
```

Here's an example where I'm moving the file to my Desktop folder from my EC2 instance
```
scp -i /Users/ewilbanks/Desktop/amazon.pem ubuntu@ec2-52-5-171-50.compute-1.amazonaws.com:/home/ubuntu/new-cloud.txt /Users/ewilbanks/Desktop/ 
```

###2. Using `wget` to download public data
What if you wanted to download that cloud.txt file *directly* onto your EC2 instance?  
After all, you downloaded it from a public dropbox link!

From your terminal window connected to your EC2 instance:
```
wget https://www.dropbox.com/s/9y41he4ol62gu0b/cloud.txt

```
`wget` stands for "web get" and it does exactly as you'd imagine - grabs data from over a network!

Enough practice.  Let's move on to the next tutorial where we'l start by getting some files we'll actually work with!

[Navigate to the Jupyter notebooks tutorial](https://github.com/ewilbanks/micdiv2017/blob/master/tutorials/2017-02-16-jupyterNotebooks.md)
