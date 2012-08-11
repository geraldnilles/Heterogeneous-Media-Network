
This project will create a heterogeneous media network for a home.

# The Computers
This network consists of 4 types of computers.

## The Leader

This will be a low power, always-on server.
All external ports will be forwarded to this server.  Therefore it will be the main web server.
Since this server will always be on, it will use either an Intel Atom or ARM CPU. Its only
purpose will be to recieve HTTP/SSH Requests and respond accordingly.  It will not store data
or perform heavy computation.  It will also manage the network's schedule.  It will wake up and put
to sleep all the other servers as needed.

## The Data
This will be a medium power NAS server.
It will run an dual core processor and contain many harddrives.  It will server files to the rest
of the network via Samba or NFS.  It will run a hardware RAID5 with MDADM.  This server will be 
awake for a scheduled period of time (5pm to 12am).  It can also be woken up on-demand through an
HTTP command.  THe Leader will manage the sleep scheudle.

## The Muscle
THis will be a high powered computation server.
It will be a 6 or 8 core processor and a small harddrive (~80 GB).  It will be waken whenever a
heavy computation is required (like transcoding video to h264).  The server will only be awake
when needed and will be put to sleep as soon as the task is completed.

## The Frontend
This will be a low powered ARM or Atom cpu that will be specialized for decoding H264 video.
There will be multiple frontend.  One for each TV in the home.  Each will run XBMC and communicate
directly with the Data server's network share.

# The Software

## Wake On LAN
The biggest reason for implementing this type of system is to save power.
For this reason, it is important that each system is capable of Waking On Lan (WOL).

When a system hibernates, it usually leaves a few ways to wake itself. 
Pressing the power button and pressing the keyboard are the most common ways of waking up a system. 
For WOL, we will want the system to also be listening to the Ethernet port for specific Wake Up packets.
When a Wakeup packet is sent to the sytem, the systme will wake from hibernation.

At this point, i do not know how to tell if a system supports WOL.
I also have not tested any of my systems.
