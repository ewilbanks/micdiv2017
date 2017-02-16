# Introduction to QIIME using ipython notebook

Navigate to your terminal that is ssh'd into the EC2 instance that you've launched using the QIIME AMI 
(what you've been working in all day).

Download the QIIME ipython notebook tutorial 

```
wget https://raw.githubusercontent.com/biocore/qiime/1.9.1/examples/ipynb/illumina_overview_tutorial_workshop_template.ipynb
```

- Now go to your internet browser that's open to your notebook server adress
- Click on the `illumina_overview_tutorial_workshop_template.ipynb`
- Work through this tutorial notebook!

There will be steps in this QIIME tutorial that a while (10-15 minutes to run).  You'll see a little astrix next to the code block that indicates it's still working.  
- To check how things are running in the terminal, you can type 
```
top
```
This will bring up a display that shows you what proceeses are running.

### When you're done working
You can either `STOP` or `TERMINATE` your instance from the EC2 console.  

Which should you choose?

#### `STOP` the instance if you want to come back and work with it using data that's in the home directory
- stopped instances save the data on the home directory (unlike terminate)
- we only pay a very small (pennies) storage fee, as opposed to the hourly rate for running the instance
- you can start up the instance again and work right from where you were
*Note that each time you start an instance you pay for 1 hour of time (~10-20 cents) even if you don't use the full hour.*

#### Terminate the instance if you don't care about saving any of the data
- Terminated instances vanish, no run fees and no storage fees
- All data associated with this instance will be **gone**
