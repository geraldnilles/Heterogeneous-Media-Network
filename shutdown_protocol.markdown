# Shutdown Protocol

This document will outline the shutdown protocol for the entire system.

## Option 1 - All Leader

The leader will load a webpage from the server it wasnt to shutdown.
During the processing of that page request, the server will run the "shutdown -h 0" command.

To do this, the www-app user will need to have permissions to run the shutdown command.  It may be a security concern to give the www-user access to this command.

I am also concerned with how the webserver will react when a shutdown command is called in the middle of a request.  It may leave the connection open and the leader will wait and timeout.

## Option 2 - Middle Man

THe leader will load a webpage from the server it want to shutdown.
This webapp will modify a file on the servers system that says its ready to shutdown.

THe server will have a periodic process that will check this file for any shutdown flags.  If the shutdown flag is set, the computer will shutdown.
