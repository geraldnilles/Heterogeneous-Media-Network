# The Data

## Hardware
A whole bunch of 1TB hard drives.  
A dual core processor.

## OS
Ubuntu Server

## Additional SW

### MDADM Software RAID
THis will manage all of the harddisks

### Samba and NFS
Used to share files with the network.

### Apache WSGI Python 
Web Server that will be used to talk with the leader.
THere will only be a few web pages:

* RAID Manager
    * View the status of the RAID array
    * Add/Remove Disks
* Halt
    * THis will be a page that when called, will halt the server
* Data Manager
    * View stats (% used)
    * Modify Samba/NFS shares
* Ping
    * This page will be used by other servers to see if the server is running.

### Watchdog
This script will ping the leader server periodically to make sure everying is ok.
If the leader script does not respond, the data will shutdown.

## Configuration

### IP Address
This server's IP address will end in 201

