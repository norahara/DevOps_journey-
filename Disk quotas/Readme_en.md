## Disk quota - theoretical and practical

### < Theoretical part />

- What is disk quota? 💿

> Disk quotas set disk usage limits for users or groups. What they are used for is to prevent servers from being filled by one user, reducing the risk of server crashes.
For example, if the server has 10 GB of space, if the disk is not quotated, one user can fill it and the server can crash.

- The answer to the question of what and how disk quotas limit is as follows:

Disk quotas usually limit 2 types of resources:

1. Block quota (disk size)

2. Inode quota (number of files)

Inode is a passport of information about a file 📄
NOT the file itself, but its description.

What does an inode store?

1. File size

2. Owner

3. Permissions

4. Creation/modification time

5. Location on disk (in which blocks)

![inode](./images/T1.png)

Inode sequence number (each file has one inode)

![inode](./images/T12.png)

2️⃣ What is a disk block?

Disk block is a real space on the disk, a part where file information is stored 📦

File information (text, video, image) is stored here

Size is usually:

4KB

8KB

The problematic situation is that if either Inode or Block runs out of memory, it will generate an error that there is no space left

### < Practical part />

- Setting disk quotas

To set disk quotas, changes and additions are made to the /etc/fstab file. Several steps must be performed before that

During this study, I completed the following tasks:
- working with logical volumes
- dividing the file system into disks
- dividing files such as /var /home into separate disks
- assigning disk quotas
- setting disk usage limits for users

The process of learning the filesystem is experimenting with these

![image](./images/T13.png)