
# Recovering Linux

## Boot errors

### ima: error communicating to tpm chip

For me, turned out to be the boot drive had a FUBAR'd journal after an unplanned outage (yes, yes, I'm using a UPS -- just doesn't help if a 30-min outage happens overnight). This fixed the boot:

At the ```(intramfs)``` prompt, type ```blkid``` to see all the drive partitions. Then go down the list of the boot drive, e.g.:

```
fsck /dev/sda1 -y
fsck /dev/sda2 -y
...
```

(and yes, ```fsck``` is the partition checking and fixing command, not something I mutter at my computers daily.) You'll likely see a bunch of recovered sectors after an unplanned outage, since Linux couldn't doo any housekeeping like it does during a normal shutdown.

If that didn't solve it, the drive has deeper issues.

