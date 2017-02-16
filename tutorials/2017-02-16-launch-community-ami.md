
We're going to launch an EC2 instance, but unlike last time where we launched a "generic" Ubuntu server,
this time we're going to launch a machine created by the QIIME team.  The benefit of doing things this way
is that your instance will have (almost) all the software we need for today pre-installed!

We'll do this by using what's called a Community Amazon Machine Image or "Community AMI".  
Click here to learn more about [what *exactly* AMIs are](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html)


- Navigate to the [EC2 management console](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#LaunchInstanceWizard:)
- Click on launch an instance
- At the left click on the sidebar that says "Community AMI"
- Under Community AMIs search for "qiime" to pull up machines that match that.  
- We want the first one circled in red below (qiime-191 - ami-1918ff72)
- You can also always find the most recent QIIME AMIs listed [here](http://qiime.org/home_static/dataFiles.html)

![Community AMI image](../img/qiime-ami-01.png)
