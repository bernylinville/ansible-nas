```bash
sudo apt update && sudo apt upgrade -y
sudo apt install linux-generic-hwe-20.04

sudo sgdisk --zap-all /dev/sdb
sudo sgdisk --zap-all /dev/sdc
sudo sgdisk --zap-all /dev/sdd
sudo sgdisk --zap-all /dev/sde
sudo sgdisk --zap-all /dev/sdf

sudo apt install zfsutils-linux
sudo systemctl enable zfs-import-scan.service
sudo sync && sudo reboot

sudo zpool create -o ashift=12 tank raidz2 ata-QEMU_HARDDISK_QM00005 ata-QEMU_HARDDISK_QM00007 ata-QEMU_HARDDISK_QM00009 ata-QEMU_HARDDISK_QM00011 ata-QEMU_HARDDISK_QM00013

sudo zpool set autoexpand=on tank
sudo zfs set atime=off tank
sudo zfs set compression=lz4 tank

sudo zfs create tank/movies
sudo zfs set recordsize=1M tank/movies
sudo zfs set compression=off tank/movies
sudo zfs set exec=off tank/movies

sudo zfs create tank/downloads
sudo zfs set exec=off tank/downloads

sudo vim /etc/cron.d/zfsutils-linux
0 2 * * 3

sudo apt install postfix
http://mhawthorne.net/posts/2011-postfix-configuring-gmail-as-relay/

sudo zfs create tank/tv
sudo zfs set recordsize=1M tank/tv
sudo zfs set compression=off tank/tv
sudo zfs set exec=off tank/tv

sudo zfs create tank/torrents

sudo zfs create tank/music
sudo zfs set recordsize=1M tank/music
sudo zfs set compression=off tank/music
sudo zfs set exec=off tank/music

sudo zfs create tank/podcasts
sudo zfs set recordsize=1M tank/podcasts
sudo zfs set compression=off tank/podcasts
sudo zfs set exec=off tank/podcasts

sudo zfs create tank/books
sudo zfs set recordsize=1M tank/books
sudo zfs set compression=off tank/books
sudo zfs set exec=off tank/books

sudo zfs create tank/audiobooks
sudo zfs set recordsize=1M tank/audiobooks
sudo zfs set compression=off tank/audiobooks
sudo zfs set exec=off tank/audiobooks

sudo zfs create tank/comics
sudo zfs set recordsize=1M tank/comics
sudo zfs set compression=off tank/comics
sudo zfs set exec=off tank/comics

sudo zfs create tank/photos
sudo zfs set recordsize=1M tank/photos
sudo zfs set compression=off tank/photos
sudo zfs set exec=off tank/photos

sudo zfs create tank/docker-data
```