# LINUX COMMANDS BY TOPIC

## Cron

### Check Crontab on all users

`# for user in $(cut -f1 -d: /etc/passwd); do crontab -u $user -l; done`

## User Linux

Create user:
    `sudo useradd user_name`

Add user to sudo or another groups
    `sudo usermod sudo/or_another_group user_name`

Auto change password on next login
    `sudo chage -d 0 user_name`

## Check Recently Modified Files

New or recently modified files may be part of the hack.

You can identify hacked files by seeing if they were recently modified.

To manually check recently modified files:

Log into your server using an FTP client or SSH terminal.
If using SSH, you can list all files modified in the last 15 days using this command:
`$ find ./ -type f -mtime -15`
If using SFTP, review last modified date column for all files on the server.
Note any files that have been recently modified.
To check recently modified files using terminal commands on Linux:

Type in your terminal:
`$ find /etc -type f -printf '%TY-%Tm-%Td %TT %p\n' | sort -r .`
If you want to see directory files, type in your terminal:
`$ find /etc -printf '%TY-%Tm-%Td %TT %p\n' | sort -r .`
Unfamiliar modifications in the last 7-30 days may be suspicious.

## Check Malware Redirection on SQL database

`select * from wp_posts where post_content like '%https://cdn.examhome.net/cdn.js%';`

## Disk

## Increase Disk

Edit the VM settings and increase the size of the disk

`sudo rescan-scsi-bus` ( if does not exist install 'scsitools')

`fdisk /dev/sdX`
press l, to list all partions
press d, to delete an existing partition (partition you would like to extend)     
press <N>, N=1, or 2 or 3 ... depends on the number to which partition is associated with     
press n, for creating a new partition     press p, for primary partition     
press <N>, N=1, or 2 or 3 ... set the number under which the partition will be associated     
input starting block number (be careful the starting number needs to match with the starting number of the partition that was deleted)     
input ending block number (for this a suggestion can be considered as true or if the partition that is created need to have -1 from the starting block number of the next next partition)     
input t, to change the Hex descriptor of the newly created partition from Linux (83) to Linux LVM (8e)     
input w, to write all changes that were made

reboot the system for the changes to take effect in the kernel

## Rsync

6 rsync Examples to Exclude Multiple Files and Directories using exclude-from
by RAMESH NATARAJAN on JANUARY 25, 2011
Rsync is very powerful tool to take backups, or sync files and directories between two different locations (or servers).

You know this already, as we presented you with practical examples on rsync earlier.

In a typical backup situation, you might want to exclude one or more files (or directories) from the backup. You might also want to exclude a specific file type from rsync.

This article explains how to ignore multiple files and/or directories during rsync with examples.

First, create a sample directory structure as shown below (with some empty files) that can be used for testing purpose.

    $ cd ~
    $ mkdir -p source/dir1/dir2
    $ mkdir -p source/dir3
    $ touch source/file1.txt
    $ touch source/file2.txt
    $ touch source/dir1/dir2/file3.txt
    $ touch source/dir3/file4.txt
The above command will create a source directory (under your home directory) with the following structure.

    source
    - file1.txt
    - file2.txt
    - dir1
    - dir2
        - file3.txt
    - dir3
    - file4.txt
  
### 1. Exclude a specific directory

If you don’t want to sync the dir1 (including all it’s subdirectories) from the source to the destination folder, use the rsync –exclude option as shown below.

    $ rm -rf destination

    $ rsync -avz --exclude 'dir1' source/ destination/
    building file list ... done
    created directory dest
    ./
    file1.txt
    file2.txt
    dir3/
    dir3/file4.txt
    Verify to make sure dir1 is not copied from source directory to destination directory.

    $ find destination
    destination
    destination/file2.txt
    destination/file1.txt
    destination/dir3
    destination/dir3/file4.txt

### 2. Exclude multiple directories that matches a pattern

The following example will exclude any directory (or subdirectories) under source/ that matches the pattern “dir*”

    $ rm -rf destination

    $ rsync -avz --exclude 'dir*' source/ destination/
    building file list ... done
    created directory destination
    ./
    file1.txt
    file2.txt
Verify the destination directory to make sure it didn’t copy any directories that has the keyword “dir” in it.

    $ find destination
    destination
    destination/file2.txt
    destination/file1.txt

### 3. Exclude a specific file

To exclude a specific file, use the relative path of the file in the exclude option as shown below.

    $ rm -rf destination

    $ rsync -avz --exclude 'dir1/dir2/file3.txt' source/ destination/
    building file list ... done
    created directory destination
    ./
    file1.txt
    file2.txt
    dir1/
    dir1/dir2/
    dir3/
    dir3/file4.txt

Verify the destination directory to make sure it didn’t copy the specific file ( dir1/dir2/file3.txt in this example).

    $ find destination
    destination
    destination/file2.txt
    destination/file1.txt
    destination/dir1
    destination/dir1/dir2
    destination/dir3
    destination/dir3/file4.txt

### 4. Exclude path is always relative

If you are not careful, you might make this mistake.

In the following example, the exclude option seems to have a full path (i.e /dir1/dir2/file3.txt). But, from rsync point of view, exclude path is always relative, and it will be treated as dir1/dir2/file3.txt. In the example below, rsync will look for dir1 under source directory (and not under / root directory).

    $rsync -avz --exclude '/dir1/dir2/file3.txt' source/ destination/

So, the above command is exactly same as the following. Just to avoid confusion (and to make it easy to read), don’t give / in front of the exclude path.

    $rsync -avz --exclude 'dir1/dir2/file3.txt' source/ destination/

### 5. Exclude a specific file type

To exclude a specific file type that has a specific extension, use the appropriate pattern. For example, to exclude all the files that contains .txt as extension, do the following.

    $ rsync -avz --exclude '*.txt' source/ destination/
    building file list ... done
    created directory destination
    ./
    dir1/
    dir1/dir2/
    dir3/

Verify the destination directory to make sure it didn’t copy the *.txt files.

    $ find destination
    destination
    destination/dir1
    destination/dir1/dir2
    destination/dir3

Note: The above is very helpful, when you want to backup your home directory, but exclude all those huge image and video files that has a specific file extension.

### 6. Exclude multiple files and directories at the same time

When you want to exclude multiple files and directories, you can always specify multiple rsync exclude options in the command line as shown below.

    $rsync -avz --exclude file1.txt --exclude dir3/file4.txt source/ destination/

Wait. What if I had tons of files that I want to exclude from rsync?

I can’t keep adding them in the command line using multiple –exclude, which is hard to read, and hard to re-use the rsync command for later.

So, the better way is to use rsync –exclude-from option as shown below, where you can list all the files (and directories) you want to exclude in a file.

First, create a text file with a list of all the files and directories you don’t want to backup. This is the list of files and directories you want to exclude from the rsync.

    $ vim exclude-list.txt
    file1.txt
    dir3/file4.txt

Next, execute the rsync using –exclude-from option with the exclude-list.txt as shown below.

    $ rm -rf destination

    $ rsync -avz --exclude-from 'exclude-list.txt' source/ destination/
    building file list ... done
    created directory destination
    ./
    file2.txt
    dir1/
    dir1/dir2/
    dir1/dir2/file3.txt
    dir3/

Verify the desitination directory to make sure the files and directories listed in the exclude-list.txt file is not backed-up.

    $ find destination
    destination
    destination/file2.txt
    destination/dir1
    destination/dir1/dir2
    destination/dir1/dir2/file3.txt
    destination/dir3

## Fixing Redirection Wordpress

widianto: Step-stepnya :
1. upgrade di docker menggunakan branch dev
2. setelah selesai push ke gitlab
3. kemudian push ke t5 or t9
4. nunggu Acc PM, setelah ACC
5. di local merge ke branch master
5. kemudian push ke prod, untuk amannya backup dulu public_html dan db, supaya mudah revert klo ada kesalahan dalam deploy.
6. done

<<<  satu lagi keingetan untuk db di prod setelah di backup jalankan perintah ini:

1. untuk melist js script yg diinput ke db jalankan query

select * from wp_posts where post_content like '% https://cdn.examhome.net/cdn.js%' ;

2. untuk menghilangkan script js di db jalankan perintah

UPDATE wp_posts SET post_content=replace(post_content,'<script src='' https://pr.uustoughtonma.org/d.js' ' type=''text/javascript''></script><script src='' https://s2.voipnewswire.net/s2.js' ' type=''text/javascript''></script><script src='' https://cdn.examhome.net/cdn.js?ver=1.0.5' ' type=''text/javascript''></script>','') WHERE post_content LIKE '% https://cdn.examhome.net/cdn.js%' ;