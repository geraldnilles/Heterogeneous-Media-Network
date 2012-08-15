# Hard Drive Backup Power

One of the most dangerous things you can do to your hard drive is to suddenly remove power.
If this happens during a write event, the HDD could get a corrupt sector.
If this hard drive is in a RAID, this could cause the entire RAID to break which is bad news.

Power outages occur randomly and there is no guarentee that this will not happen to my RAID.

## UPS
There are devices called UPS (Uninteruptible power supplies) which will continue to provide power, but these devices can be expensive and a little overkill.
THis device looks like a power strip and will continue to provide power to the entire system for a few minutes.

## HDD Only Backup
A cheaper idea would be to only provide backup power to the hard drives.
THe goal would be to provide jsut enough energy so the HDDs can complete any pending writes stored in the cache.

The circuit would be:
PSU ==> UVLO Loadswitch ==> Capacitor Bank ==> UVLO Loadswitch ==> HDDs

During normal operation, the capacitor bank will be charged by the PSU.
When the power goes out, the PSU voltage will drop and the first load switch will prevent current flow from the Capacitor bank back to the PSU rail.
THe capacitor bank will not supply the HDDs.
WHen the capacitor bank voltage drops below a cirtain theshold, the 2nd loadswitch will close and effectivly kill power to the HDDs.

If evertying goes to plan, the HDD will no longer be writing anything by the time the capacitor bank runs out of juice.  
