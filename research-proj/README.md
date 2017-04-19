

------
Setting up jupyter notebook server on a new machine

wget https://repo.continuum.io/archive/Anaconda3-4.3.1-Linux-x86_64.sh
bash Anaconda3-4.3.1-Linux-x86_64.sh
# added to anaconda3 folder bin to path, 
conda upgrade notebook
jupyter notebook --generate-config
# Writing default config to: /home/ubuntu/.jupyter/jupyter_notebook_config.py

## opened notebook server
jupyter notebook --ip=* --no-browser
## in parallel screen ran
jupyter notebook list
## used token to get into notebook
## ran the following as a cell in ipython notebook
  from IPython.lib import passwd
  password = passwd("secret")
  password

Edited config file to be the one in this repo, with password specific to the one generated previously

jupyter must be launched with jupyter notebook --ip=* --no-browser  
trying to put this into the config file isn't working :(

