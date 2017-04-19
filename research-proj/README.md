# Notes on working with Tessa to set up the smrt-analysis ami on AWS
* launching 2.3.0 smrtanalysis ami
* having issues since its running an old linux OS (lucid)
* couldn't apt-get install anything

### Below was what we ran to get it to update from lucid -> precise
`lsb_release –a` shows you the version of the OS you're running

```
sudo apt-get update
do-release-upgrade
sudo apt-get install -o APT::Immediate-Configure=false -f apt python-minimal
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install default-jre
```

configuring and setting up with github!
```
sudo apt-get install git
git clone https://github.com/ewilbanks/micdiv2017.git
```

### tips and reminders for working with git from commandline
to check if your repo is up to date
```
git status
````

To add new files to your repo : `git add filename`
To get those changes into your centralized git repo
```
git commit -m "some helpful comment about your commit changes"
git push
```

To update your local repo from the server:
```
git pull
```
