# Notes on working with Tessa to set up the smrt-analysis ami on AWS
* launching 2.3.0 smrtanalysis ami
* having issues since its running an old linux OS (lucid)
** couldn't apt-get install anything

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
