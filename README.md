# Backoops

My homeserver backup system? Whatever

I couldn't find any automatic and **reliable** backup solution so I've created my own lol


## Architecture

```
                            Disks

 ___________         ____________________________________
| Host OS   |       | Data & files (any fs) single disk  |
| (any fs)  |       | Two backup options                 |
 '''''' ''''         ''''''''  ''''''''''''''''''''''''''
      |                   |                         |
	  |                   |                         |
	 \|/                 \|/                       \|/
Not backed up        each 3 days             when powered on
                          |                         |
					      |                         |
						 \|/                       \|/
				   ________________         __________________
				  | btrfs RAID 1   |       | Off-site backups |
				  |----------------|       | btrfs with up to |
				  | with snapshots |       | 10 snapshots     |
				  | from last 90d  |       | single disk      |
				   ''''''''''''''''         ''''''''''''''''''
```


## Setup

Setup partitions, permissions, blah blah blah

Just run `backup.py` file, it will run infinitely and do backups automagically.
Add it as systemd service for example
