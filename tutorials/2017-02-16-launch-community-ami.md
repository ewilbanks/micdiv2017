
We're going to launch an EC2 instance, but unlike last time where we launched a "generic" Ubuntu server,
this time we're going to launch a machine created by the QIIME team.  The benefit of doing things this way
is that your instance will have (almost) all the software we need for today pre-installed!

We'll do this by using what's called a Community Amazon Machine Image or "Community AMI".  
Click here to learn more about [what *exactly* AMIs are](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html)

You should be able to follow below but if you're lost 
or need to set the key-pair for the first time, you can review [EC2 launch instructions here](http://angus.readthedocs.io/en/2016/amazon/index.html)

### Navigate to QIIME's community AMI
- Navigate to the [EC2 management console](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#LaunchInstanceWizard:)
- Be sure you are in the US East zone (North Virginia)
- Click on launch an instance
- At the left click on the sidebar that says "Community AMI"
- Under Community AMIs search for "qiime" to pull up machines that match that.  
- We want the first one listed below (qiime-191 - ami-1918ff72)
- Click Select
- You can also always find the most recent QIIME AMIs listed [here](http://qiime.org/home_static/dataFiles.html)

![Community AMI image](../img/qiime-ami-01.png)

- Launch this AMI
- Select m1.large as the instance type for today 
- Click through to review & launch  (but don't finalize launch yet)

### Set a new security rule for your instance 
To log into your QIIME instance, you’ll need to have ssh access (i.e., port 22), which is enabled by default.
Later in the tutorial today, you'll want to use IPython Notebook on your instance, so you need to add another security rule. You can do this by clicking the link circled in red below:
![Edit security rules](../img/qiime-ami-02.png)

- Then click `Add rule`
- For the new secturity rule fill out the fields as shown below
  - The Type should be Custom TCP Rule
  - the Protocol should be TCP
  - the Port Range should be 8888
  - the Source should be Anywhere.
![New security rule](../img/qiime-ami-03.png)

### Now log into your QIIME EC2 instance
- On the EC2 console, look up the public DNS for your instance.
- Open a terminal window (of Mobaxterm for Windows users) and `ssh` into your instance

### *Need another walk through of how to log into you EC2 instance?*
*Keep reading, otherwise move on to the next section!*
[Navigate to the data transfer section of tutorial](https://github.com/ewilbanks/micdiv2017/blob/master/tutorials/2017-02-16-qiime-startup.md)

####0. Find your EC2's Public DNS:
Before you can connect to your EC2 instance you first need to find its Public DNS. This essentially acts as an address for your EC2 instance so that your local computer can access it. Go to [AWS](http://aws.amazon.com/) and sign into the Console. Select EC2, and then view your running instances. On this page, click on your instance and find it's public DNS under the "Description" tab.

![PublicDNS](https://github.com/ewilbanks/2015-tutorials/blob/master/img/EC2_Public_DNS.png?raw=true)

In the image above the full Public DNS of the highlighted instance is **ec2-52-5-171-50.compute-1.amazonaws.com**

####1. Open a Terminal:
- **Windows users** Use MobaXterm [here](http://mobaxterm.mobatek.net/download.html) to use as your terminal. 
- **MAC Users:** Terminal is under: Applications --> Utilities
- **Linux Users:** Press Ctrl + Alt + t

You will need to know the location of your **key pair** you created when you launched your instance.  Usually this will be in your "Downloads" folder, but you may want to move it elsewhere.
 
```
cd /Downloads
```

You will need to know what your Public DNS is for your EC2 Instance.

####2. Change your keyfile permisions to read only:

```
chmod 400 **/path/to/your/keyfile/**.pem
```
This command will adjust the permissions on your keyfile so that it cannot be edited. This is important because if the keyfile is edited or changed, it will no longer allow access to the EC2 instance.

####3. Connecting to your EC2 instance using ssh:

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

OK - now you're really ready.  

[Navigate to the data transfer section of tutorial](https://github.com/ewilbanks/micdiv2017/blob/master/tutorials/2017-02-16-qiime-startup.md)


