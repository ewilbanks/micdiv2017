# Notes on working with Tessa to set up Cerulean to run on the smrt-analysis ami w/ AWS
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
------
## Working on getting dependencies for cerulean working properly
* Need `blasr` in the system path, initially wasn't 
* Found folder of executable files and adding to .bashrc `$PATH`
```
#adding smrt analysis executables to path
export PATH="/opt/smrtanalysis/current/analysis/bin/:$PATH"
```

#### Installing PB suite
```
wget https://downloads.sourceforge.net/project/pb-jelly/PBSuite_15.8.24.tgz
tar -xvzf PBSuite_15.8.24.tgz
```
* No install required, just a matter of adding the appropriate paths and installing one other dependency
* Using anaconda package manager
* NOTE: this will _only_ run with Python 2.7 _not_ with Python 3 (must be using anaconda2)
```
conda install -c anaconda networkx
```
* Need to edited my `~/.bashrc` file to include a PYTHONPATH environmental variable which PB-suite needs.  
* I found all the appropriate python libraries by doing the following from within an interactive python session
```
$ python
Python 2.7.13 |Anaconda 4.3.1 (64-bit)| (default, Dec 20 2016, 23:09:15)
[GCC 4.4.7 20120313 (Red Hat 4.4.7-1)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
Anaconda is brought to you by Continuum Analytics.
Please check out: http://continuum.io/thanks and https://anaconda.org
>>> import sys
>>> print sys.path
```
* Using the output of that command above as the info, I added the following lines to the `~/.bashrc` file
* Note that I also added the PB-suite's install location at the end
* Also added the bin file location for PB-suite and the `SWEETPATH` environmental variable that it needed
```
### pythonpath
export PYTHONPATH="home/ubuntu/anaconda2/pkgs:/home/ubuntu/anaconda2/lib/python27.zip:/home/ubuntu/anaconda2/lib/python2.7:/home/ubuntu/anaconda2/lib/python2.7/plat-linux2:/home/ubuntu/anaconda2/lib/python2.7/lib-tk:/home/ubuntu/anaconda2/lib/python2.7/lib-old:/home/ubuntu/anaconda2/lib/python2.7/lib-dynload:/home/ubuntu/anaconda2/lib/python2.7/site-packages:/home/ubuntu/PBSuite_15.8.24"
# adding pbsuite
export PATH="$PATH:/home/ubuntu/PBSuite_15.8.24/bin"
export SWEETPATH=/home/ubuntu/PBSuite_15.8.24
```

### Testing that PB-suite is properly installed
* Go to the toy data example for Jelly and edit the `Procotol.xml` file such that paths match appropriate location for your system
* For me that was the following:
```
$ cat Protocol.xml
<jellyProtocol>
    <reference>/home/ubuntu/PBSuite_15.8.24/docs/jellyExample/data/reference/lambda.fasta</reference>
    <outputDir>/home/ubuntu/PBSuite_15.8.24/docs/jellyExample/</outputDir>
    <blasr>-minMatch 8 -minPctIdentity 70 -bestn 1 -nCandidates 20 -maxScore -500 -nproc 4 -noSplitSubreads</blasr>
    <input baseDir="/home/ubuntu/PBSuite_15.8.24/docs/jellyExample/data/reads/">
        <job>filtered_subreads.fastq</job>
    </input>
</jellyProtocol>
```
* Now test Jelly with the following commands
```
Jelly.py setup Protocol.xml
Jelly.py mapping Protocol.xml
Jelly.py support Protocol.xml
Jelly.py extraction Protocol.xml
Jelly.py assembly Protocol.xml
Jelly.py output Protocol.xml
```
