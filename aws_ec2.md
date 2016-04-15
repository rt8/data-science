# EC2

## Setup EC2 Instance Store (ephemeral storage)
All EC2 instances are provisioned with instance stores that provide "temporary" block storage for your instance.  
These will be deleted when the EC2 instanced is stopped or terminated.  You should use Elastic Block Storage (EBS) if you need to save data when EC2 is stopped.
The instance stores are located on disks that are physically attached to the host computer.
http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html

See volumes that are formatted and mounted
```sh
$ df -lh     
```

Show available storage (instance stores) provisioned by AWS
```sh
$ sudo fdisk -l  
$ lsblk           # also try this to view any volumes that were mapped at launch but not formatted and mounted
```

Check file system types that are currently mounted.  Most of them will be ext4 format
```sh
$ sudo mount -l
```
Create directory to mount the device (instance store), and create file system on the device
```sh
$ sudo mkdir /mntX                    # X = 1,2,3...etc
$ sudo mkfs -t ext4 /dev/ZZZ          # ZZZ is the path to storage obtained from fdisk -l (above)
```

Mount storage
```sh
$ sudo mount -t ext4 /dev/ZZZ /mntX
```

Now you can use the storage at path **/mntX**

