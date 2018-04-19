<p align="center">
  <img src="https://raw.githubusercontent.com/dipc-cc/dcrab/master/aux/logos/DCRAB_logo.png" alt="DCRAB Logo"/>
</p>

DCRAB monitorizes submitted jobs into a scheduler system and creates a real time report based on its execution. The report displays some statistics and charts, such as CPU usage, memory consumed by all the processes, Infiniband statistics etc, which may help to understand the behavior of the job at anytime.

### How to use it

To use DCRAB you need only to 'start' and 'finish' it with the following commands in your script:
```bash
export DCRAB_PATH=/PATH_TO_DCRAB/src/
export PATH=$PATH:$DCRAB_PATH
dcrab start

##################################
#    BLOCK OF CODE TO MONITOR    #
##################################

dcrab finish
```

### Why DCRAB?

The first D is of Donostia International Physics Center Foundation (DIPC), who are the main developers of the software. The 'crab' part is an acronym of 'Control and Report Application in Bash' but also is related to the animal. The reason is because this monitoring tool, like a crab grabbing its food, grabs the processes associated in the execution to collect the data. Furthermore, there is an analogy between a crab's claw and the way DCRAB monitors the processes with 'start' and 'finish' commands because it 'catches' the block of code to monitor inside this commands like a crab holds everything inside its claws.

### PROS

  - Real time monitorization. The report file is continuously updating so if the job fails the report will be completed up to there
  - Monitors at PID level which allows to collect data only of the processes generated inside its 'start' and 'finish' statements. This allows to monitor different jobs in the same node
  - All data collected in a single html file
  - No compilation required
  - Easy to use in a script because only two sentences are required to monitor processes

### Monitoring modules added

All this modules monitor always the processes generated by the job and creates a plot for each node. Modules available are listed below:

  - CPU used
  - Memory usage 
  - Infiniband statistics (of the entire node)
  - Processes IO statistics
  - NFS usage (of the entire node)
  - Disk IO statistics (of the entire node)
  - Internal report statistics for sysadmins (IB and disk IO)

### Requirements/Limitations

  - Supports multinode statistics (only for MPI jobs)
  - PBS scheduler requirements:
    - DCRAB report directory will be created in the working directory (where the job was submitted with 'qsub')
    - The option "#PBS -l mem=" must be written explicitly in the submission script for the memory data plot and the memory must be in GB
    - The option "#PBS -l nodes=x:ppn=y" must be written explicitly in the submission script to calculate elapsed and remaining times

### Coming features

  - Configuration file to customize execution
  - Execution without scheduler 
  - Beegfs usage
  - MPI comunication statistics
  - Support for Slurm
