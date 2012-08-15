# The Data
This computer will be used for computationally heavy tasks.

## Hardware
AMD 3GHz X6 processor.

## OS
Ubuntu Server

## Additional SW

### FFMpeg / HandBrake
It will need to be able to encode and decode many video and audio codecs.

### Samba and NFS
Used to receive files to convert.

There will be an INBOX folder which takes raw input files that will be transcoded.
There will also be an OUTBOT folder for generic encoding tasks.

### Apache WSGI Python 
Web Server that will be used to talk with the leader.
THere will only be a few web pages:

* Halt
    * THis will be a page that when called, will halt the server
* Data Manager
    * View stats (% used)
    * Modify Samba/NFS shares
* Transcode Manager
    * View and Modify the Transcode Queue
    * Start and stop transcoding

## Configuration

### IP Address
This server's IP address will end in 202

