
# The Leader
This computer will control all of the others.
This computer will be very low power (under 10 Watts peak) and will always be on and connected to the internet.
It will have the ability to power on and shut down all other servers.
For this reason, the main apache server will be hosted on this box.

## Hardware
This server will be an Asus Eee Netbooks.
More specifically it is the Asus Eee 1001P.
It has a dual-core 1.6GHz Atom CPU (I want to say the N450?)
When not in higher power modes, the CPU can scale back to 1GHz to save power.

Another handy fact about this is that this server has a battery.  SO if  power goes out, this server will never die :).

## OS
This computer will have Ubuntu Server as its base.

## Additional Software
### Apache WSGI Python Server
Webpages will be hosted using Apache's daemon and will be scripted using Python.
The mod-python package must be installed.

### MySQL
The main MySQL database will be hosted and served by this PC

### WakeOnLan
In order to wake up other devices, the wakeonlan package will need to be installed.
I will also look to see if its possible to send this magic packet using pure python.
According to Wikipedia, the WOL packet can be set with any network protocol.
The format is as follows:

    0xFF 0xFF 0xFF 0xFF 0xFF 0xFF ; 6 bytes of FF
    [MAC address]                 ; the target MAC address
    [MAC address]
    [MAC address]
    ...
    [MAC address]                 ; Repeated 16 times

The total should be 102 bytes.

Traditionally, the packet is sent using a UDP datagram to port 7 or port 9.

The python code is as follows:

    import socket
    s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    s.setsockopt(socket.SOL_SOCKET, socket.SO_BROADCAST,1)
    s.sendto('\xff'*6 + '\x00\x02\xb3\x07\xb6\xd1'*16, ('192.168.0.255', 80))

In this example code, you will need to change the MAC address and probably need to change the broadcast address to match your network.

### Server Scheduler
A custom daemon process will need to be written that powers on and off the other servers as needed.
To start, we will power on both servers at 5pm and powe them down at 2am.

Power on will be done by sending a WoL packet.

Power off will be done by sending an HTTP request to the server that is hard wired to halt it.

To take it to the next level, we can also have the daemon ping the other servers to make sure they are awake or asleep.



## Configuration

### IP Address
This computer will have a static IP address ending in 200.

### Apache
[ENter apache config here]
