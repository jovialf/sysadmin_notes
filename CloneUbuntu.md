# Clone Ubuntu Server 24.04.1

### Clone menggunakan RSYNC
Pada kasus kali ini clone dari remote server ke server lokal yang sudah di installasi OS Ubuntu 24.04 dengan mengskip beberapa direktori dan file.
Yang perlu di perhatikan adalah skip direktori /dev /proc /sys /run /etc/netplan dan skip file /etc/fstab.
```
sudo rsync -aAXv \
--exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found","/home/admin","/etc/netplan/*","/etc/hostname","/etc/hosts","/etc/fstab"} \
--delete \
-e "ssh -p 2232" root@10.10.10.10:/ / \
--progress
```
Setelah sync selesai, restart server untuk perbaiki grub.
```
init 6
```

### Perbaiki grub dan boot menggunakan bootable ubuntu
Masuk ke shell menggunakan bootable ubuntu
```
mount /dev/ubuntu-vg/ubuntu-lv /mnt
mount /dev/sda2 /mnt/boot
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
```
Pada kasus ini, partisi root ada pada LVM dan partisi boot ada pada sda2.
Setelah mount paritisi, masuk chroot ke /mnt
```
chroot /mnt
```
Kemudian reinstall group dan update konfigurasi initramfs
```
grub-install /dev/sda
update-initramfs -c -k all
update-grub
```
Restart Server, apabila tidak ada kendala maka seharusnya server sudah boot normal.
```
init 6
```
