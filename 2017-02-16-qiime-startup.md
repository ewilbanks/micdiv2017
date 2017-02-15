# Getting booted up with our jupyter notebooks and our tutorial for the day
Authored by Lizzy Wilbanks for Swarthmore College BIOL133, Spring 2017
using material adapted from a tutorial in EDAMAME: Explorations in Data Analysis for Metagenomic Advances in Microbial Ecology 2015
[EDAMAME-2015 EC2-files tutorial](https://github.com/edamame-course/2015-tutorials/blob/master/final/2015-06-22-EC2_Connection_FileTransfer.md)

Today's tutorial will introduce you to a few important topics, including HOW TO:
- Transfer files between your AWS EC2 instance and your laptop using `scp`
- Download publicly-hosted data to an EC2 instance using `wget`  
- Use Jupyter notebooks to follow tutorials or take kickass computational notes
- Start using QIIME, the major software pipeline for analyzing high throughput 16S rRNA gene sequence data

## Launch an EC2 instance 
This should be the same as last time! Click [here for the reminder tutorial of how to do this] (http://angus.readthedocs.io/en/2016/amazon/index.html)
Make sure you're in the US East "north Virginia" region.
[Amazon EC2 console] (https://console.aws.amazon.com/ec2)

***
##Windows users
Download MobaXterm [here](http://mobaxterm.mobatek.net/download.html) to use as your terminal. 

##Mac OS & Linux Users, connecting to your Amazon EC2 instance at the command line is pretty easy.
###0. Find your EC2's Public DNS:
Before you can connect to your EC2 instance you first need to find its Public DNS. This essentially acts as an address for your EC2 instance so that your local computer can access it. Go to [AWS](http://aws.amazon.com/) and sign into the Console. Select EC2, and then view your running instances. On this page, click on your instance and find it's public DNS under the "Description" tab.

![PublicDNS](../img/EC2_Public_DNS.png)

In the image above the full Public DNS of the highlighted instance is **ec2-52-5-171-50.compute-1.amazonaws.com**

###1. Open a Terminal:

**MAC Users:** Terminal is under: Applications --> Utilities
**Linux Users:** Press Ctrl + Alt + t

You will need to know the location of your **key pair** you created when you launched your instance.  Usually this will be in your "Downloads" folder, but you may want to move it elsewhere.

```
cd /Downloads
```

You will need to know what your Public DNS is for your EC2 Instance.

###2. Change your keyfile permisions to read only:

```
chmod 400 **/path/to/your/keyfile/**.pem
```
This command will adjust the permissions on your keyfile so that it cannot be edited. This is important because if the keyfile is edited or changed, it will no longer allow access to the EC2 instance.

###3. Connecting to your EC2 instance using ssh:

```
ssh -i **/path/to/your/keyfile/**eda.pem ubuntu@"your public DNS"
```

On your first login, you may get a prompt stating that the host authenticity cannot be established, are you sure you want to continue?  Yes, you really do.

SUCCESS! You have now logged into your computer in the cloud!

###4. After the first login

After the first login to the EC2, you do not need to repeat the chmod to change permissions for the key.
Every time you start an previously-stopped EC2 instance, there will be a new Public DNS.  To connect to the EC2 after the first login, copy and paste that new Public DNS in the corresponding place below:

```
ssh -i **/path/to/your/keyfile/**EDAMAME.pem ubuntu@"your public DNS"
```
###5. Transferring files to and from the EC2

Next we will go over how to copy a file from your personal computer to your EC2 instance using `scp`. The usage is very similar to `ssh`.  

Download the following file onto your laptop's Desktop by clicking [this link] (https://www.dropbox.com/s/9y41he4ol62gu0b/cloud.txt?dl=0)

Now we're going to copy this file you downloaded from your laptop onto the remote EC2 machine.  
To do this start a new terminal window.  
**NOTE** This new window is **NOT** connected to the EC2.
Verify this by entering the command below
``` pwd```

Start a new terminal window before executing the command below.
```
scp -i /Users/ewilbanks/Desktop/amazon.pem /Users/ewilbanks/Desktop/cloud.txt ubuntu@ec2-52-5-171-50.compute-1.amazonaws.com:/home/ubuntu/
```
Note

(https://www.dropbox.com/s/9y41he4ol62gu0b/send-me-to-the-cloud.txt)
