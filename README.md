The SystemTap script `watchdog.stp` is good for finding a culprit that might accidentally cat or grep the `/dev/watchdog`.
Usually this results in a "Watchdog did not stop!" message in the the journal or kernel ring buffer. 

However it may not catch a culprit that you do not realize is interacting with the watchdog properly.
In some environments or situations where it not clear which program is interacting with the watchdog,
it can be hard to find which tasks are opening and closing the watchdog appropriately. 

Running `./probe1.stp ; ./probe2.stp` will show this and be very verbose about which tasks are opening 
or closing the file, or even adjusting the status in the kernel's watchdog device structure!.
