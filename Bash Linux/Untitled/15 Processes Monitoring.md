
### Ownership of running processes

### Launching a process from command line

`control + c`
`control + z` 


# Monitoring Process

To see what the a process is doing.

### GUI Monitoring Tools
System Monitor
`gnome-system-monitor` command to launch from CLI

There are two versions, one for Gnome and another for KDE.


### Command line monitoring tools

`top` `ps`

#### `top`
`top` program when launched outputs and remains running. It is an interactive program that updates its output in specified refresh rate (default 3 sec).
This can be altered using `-d s.t`  s is seconds and t is tenth of second
`-d 1` update every second 
`-d 0.5` `-d 0.0001`

```bash
sujith@sujith-Latitude-7490:~$ top -d 5

top - 18:37:00 up  2:35,  1 user,  load average: 0.15, 0.25, 0.25
Tasks: 251 total,   1 running, 250 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.0 us,  0.9 sy,  0.0 ni, 98.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
MiB Mem :   7818.0 total,   5118.5 free,   1647.7 used,   1641.4 buff/cache     
MiB Swap:   4096.0 total,   4096.0 free,      0.0 used.   6170.4 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND  
   1559 sujith    20   0 4872356 281168 127100 S   7.8   3.5   3:29.14 gnome-s+ 
   3386 sujith    20   0  554448  52336  41552 S   3.0   0.7   0:03.12 gnome-t+ 
    234 root     -51   0       0      0      0 S   1.8   0.0   0:02.40 irq/51-+ 
   2431 sujith    20   0 1159.6g 269780 129124 S   0.6   3.4  14:18.19 obsidian 
   4964 sujith    20   0   14536   5760   3584 R   0.6   0.1   0:00.25 top      
    760 systemd+  20   0   21584  12544  10368 S   0.4   0.2   0:05.00 systemd+ 
   1749 sujith    20   0  388872  11756   6784 S   0.4   0.1   0:00.85 ibus-da+ 
   2412 sujith    20   0   32.6g 133844  97160 S   0.4   1.7   4:00.22 obsidian 
   2750 root      20   0       0      0      0 I   0.4   0.0   0:05.31 kworker+ 
   2921 root      20   0       0      0      0 I   0.4   0.0   0:02.67 kworker+ 
     17 root      20   0       0      0      0 I   0.2   0.0   0:01.45 rcu_pre+ 
     79 root     -51   0       0      0      0 S   0.2   0.0   0:21.71 irq/9-a+ 
    114 root       0 -20       0      0      0 I   0.2   0.0   0:07.62 kworker+ 
    184 root       0 -20       0      0      0 I   0.2   0.0   0:00.18 kworker+ 
    761 systemd+  20   0   91044   7680   6784 S   0.2   0.1   0:04.19 systemd+ 
   2074 sujith    20   0  236772   7040   6528 S   0.2   0.1   0:00.15 ibus-en+ 
   2263 sujith    20   0 1156.1g 160496 124608 S   0.2   2.0   2:12.02 obsidian 
```

`-H` to show threads
`-i` to show idle process 
`-u username` to show process started by that username
`-n #` where hash is integer to indicate the number of refreshes that top should perform before terminating. `top -n 10`

***Keystroke commands for `top`***
A - to use alternative display mode
d - to change the interval time
i - Turn on off including idle processes
`f, o` - to add remove or alter display order
`l` - to on off load statistics
t - to on off task statistics
m - to on off memory statistics
H - Show threads
U - show specified user owned processes only
n - show only specified number of processes

q - quit


#### `ps`
`ps` command provides a detailed examination of the running process as a snapshot and is not interactive. Displays and exits.
Without any options, the only process displayed is `bash`

Lots of options to get what is needed but complex
___


Orphans, adoption from `systemd`
zombies, sleeping parent, killing