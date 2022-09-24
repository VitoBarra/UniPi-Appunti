# Accesso al disco e performance

12.1.1 Disk Access and Performance
Operating systems send commands to a disk to read or write one or more consecutive
sectors. A disk’s sectors are identified with logical block addresses (LBAs) that specify the
surface, track, and sector to be accessed.
To service a request for a sequence of blocks starting at some sector, the disk must first
seek to the right track, wait for the first desired sector to rotate to the head, and then
transfer the blocks. Therefore, the time for a disk access is:
disk access time = seek time + rotation time + transfer time
Seek. The disk must first seek — move its arm over the desired track. To seek, the
disk first activates a motor that moves the arm assembly to approximately the right
place on disk. Then, as arm stops vibrating from the motion of the seek, the disk
begins reading positioning information embedded in the sectors to determine exactly
where it is and to make fine-grained positioning corrections to settle on the desired
track. Once the head has settled on the right track, the disk uses signal strength and
positioning information to make minute corrections in the arm position to keep the
head over the desired track.
A request’s seek time depends on how far the disk arm has to move.
A disk’s minimum seek time is the time it takes for the head to move from one track to
an adjacent one. For short seeks, disks typically just “resettle” the head on the new
track by updating the target track number in the track-following circuitry. Minimum seek
times of 0.3–1.5 ms are typical.
If a disk is reading the tth track on one surface, its head switch time is the time it would
take to begin reading the tth track on a different surface. Tracks can be less than a
micron wide and tracks on different surfaces are not perfectly aligned. So, a head
switch between the same tracks on different surfaces has a cost similar to a minimum
seek: the disk begins using the sensor on a different head and then resettles the disk
on the desired track for that surface.
A disk’s maximum seek time is the time it takes the head to move from the innermost
track to the outermost one or vice versa. Maximum seek times are typically over 10 ms
and can be over 20 ms.
A disk’s average seek time is the average across seeks between each possible pair of
tracks on a disk. This value is often approximated as the time to seek one third of the
way across the disk.
Beware of “average seek time”
Although the name average seek time makes it tempting to use this metric when estimating the time it
will take a disk to complete a particular workload, it is often the wrong metric to use. Average seek time — the average across seeks between each possible pair of tracks on disk — was defined this way to
make it a well-defined, standard metric, not because it is representative of common workloads.
The definition of average seek time essentially assumes no locality in a workload, so it is very nearly a
worst-case scenario. Many workloads access sectors that are likely to be near one another; for
example, most operating systems attempt to place files sequentially on disk and to place different files
in a directory on the same track or on tracks near one another. For these (common) workloads, the
seek times observed may be closer to the disk’s minimum seek time than its “average” seek time.
The demise of the cylinder
A cylinder on a disk is a set of tracks on different surfaces with the same track index. For example, on
a 2-platter drive, the 8th tracks on surfaces 0, 1, 2, and 3 would form the 8th cylinder of the drive.
Some early file systems put related data on different surfaces but in the same cylinder. The idea was
that data from the different tracks in the cylinder could be read without a requiring a seek. Once a
cylinder was full, the file system would start placing data in one of the adjacent cylinders.
As disk densities have increased, the importance of the cylinder has declined. Today, a disk’s tracks
can be less than a micron wide. To follow a track at these densities, a controller monitors the signals
from a disk’s head to control the disk arm assembly’s motor to keep the head centered on a track.
Furthermore, at these densities, the tracks of a cylinder may not be perfectly aligned. As a result, when
a disk switches disk heads, the new head must center itself over the desired track. So, switching heads
within a cylinder ends up being similar to a short 1-track seek: the controller chooses the new
cylinder/track and the disk head settles over the target track. Today, accessing different tracks within
the same cylinder costs about the same as accessing adjoining tracks on the same platter.
Rotate. Once the disk head has settled on the right track, it must wait for the target
sector to rotate under it. This waiting time is called the rotational latency. Today, most
disks rotate at 4200 RPM to 15,000 RPM (15 ms to 4 ms per rotation), and for many
workloads a reasonable estimate of rotational latency is one-half the time for a full
rotation — 7.5 ms–2 ms.
Once a disk head has settled on a new track, most disks immediately begin reading
sectors into their buffer memory, regardless of which sectors have been requested.
This way, if there is a request for one of the sectors that have already passed under
the disk head, the data can be transferred immediately, rather than having to delay the
request for nearly a full rotation to reread the data.
Transfer. Once the disk head reaches a desired sector, the disk must transfer the data
from the sector to its buffer memory (for reads) or vice versa (for writes) as the sectors
rotate underneath the head. Then, for reads, it must transfer the data from its buffer
memory to the host’s main memory. For writes, the order of the transfers is reversed.
To amortize seek and rotation time, disk requests are often for multiple sequential
sectors. The time to transfer one or more sequential sectors from (or to) a surface
once the disk head begins reading (or writing) the first sector is the surface transfer
time.
On a modern disk, the surface transfer time for a single sector is much smaller than
the seek time or rotational latency. For example, disk bandwidths often exceed 100
MB/s, so the surface transfer time for a 512-byte sector is often under 5 microseconds
(0.005 ms).
Because a disk’s outer tracks have room for more sectors than its inner tracks and
because a given disk spins at a constant rate, the surface transfer bandwidth is often
higher for the outer tracks than the inner tracks.
For a disk read, once sectors have been transferred to the disk’s buffer memory, they
must be transferred to the host’s memory over some connection such as SATA (serial
ATA), SAS (serial attached SCSI), Fibre Channel, or USB (universal serial bus). For
writes, the transfer goes in the other direction. The time to transfer data between the
host’s memory and the disk’s buffer is the host transfer time. Typical bandwidths range
from 60 MB/s for USB 2.0 to 2500 MB/s for Fibre Channel-20GFC.
For multi-sector reads, disks pipeline transfers between the surface and disk buffer
memory and between buffer memory and host memory; so for large transfers, the total
transfer time will be dominated by whichever of these is the bottleneck. Similarly, for
writes, disks overlap the host transfer with the seek, rotation, and surface transfer;
again, the total transfer time will be dominated by whichever is the bottleneck.
