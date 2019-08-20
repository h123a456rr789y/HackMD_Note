---
title: APM Deployment
tags: Intern, APM
description:
---


# APM Deployment
## APM structure
![](https://i.imgur.com/JUzdwU5.jpg)

## Operating Environment Template
- Host OS: Ubuntu Desktop 16.04 LTS
- Guest(VM) OS: Ubuntu Desktop 16.04 LTS(CN)(kernel 4.15.0-55) & 14.04 LTS (Test VM)(kernel 4.4.0-87)
- All of Login Account (Account Type): test (Administrator)
- All of Login Password: test
- Additional Installed Packages: vim, openssh-server, desktop sharing, folder sharing

## Install and Run KVM
- Install the packages of KVM, then reboot
```
shell > sudo apt install qemu-kvm libvirt-bin bridge-utils virt-manager
```

## Setup Passwordless with ssh
- Set up passwordless connection between (CN&SN) and (SN & TestVM) bidirectionally
- Passwordless for both root and user:
    - test <-> test
    - test <-> root
    - root <-> test
    - root <-> root
- Set up: PermitRootLogin yes and ssh restart
```
sudo vim /etc/ssh/sshd_config
sudo service ssh restart
sudo service ssh status
```
![](https://i.imgur.com/4B0dki4.png)

- Change Root password 
```
sudo passwd root
``` 
- ssh-keygen in root and ssh-copy-id to the target
```
ssh-keygen
# Enter to the end
ssh-copy-id root@target_ip
# enter root-password
```
- Root 間有成功做到passwordless 則 user間就也有passwordless

## Change to the Correct Kernel Version
- Use follow commmand to check your OS & kernel infomation
```
lsb_release -a

uname -a
```
- Install 4.15.0-55 kernel image, headers & modules-extra and update initramfs & grub, then reboot
```
shell > sudo apt install linux-image-4.15.0-55-generic
shell > sudo apt install linux-headers-4.15.0-55-generic
shell > sudo apt install linux-modules-extra-4.15.0-55-generic
shell > sudo update-initramfs -u -k all
shell > sudo update-grub
shell > sudo reboot
```
- Install 4.4.0-87 kernel image, image-extra & headers and update initramfs & grub, then reboot
```
shell > sudo apt-get install linux-image-4.4.0-87-generic
shell > sudo apt-get install linux-image-extra-4.4.0-87-generic
shell > sudo apt-get install linux-headers-4.4.0-87-generic
shell > sudo update-initramfs -u -k all
shell > sudo update-grub
shell > sudo reboot
```

- Edit string in /etc/default/grub, then save
```
/*edit from
GRUB_DEFAULT=0
save to
GRUB_DEFAULT=saved */

shell > sudo vim /etc/default/grub
shell > awk -F\' '$1=="menuentry " || $1=="submenu " {print i++ " : " $2}; /\tmenuentry / {print "\t" i-1">"j++ " : " $2};' /boot/grub/grub.cfg

# Select the kernel version you want to 

shell > sudo grub-set-default '1>2'
shell > sudo update-grub
```

## Settings Before Running APM Code
- Change the path in `_amd.conf` in apm-kernel_4.15.0-55-generic/am1/amdeploy
![](https://i.imgur.com/L8BZebC.png)

- Change the deployed info in `_amnodespec.yaml` in apm-kernel_4.15.0-55-generic/am1/amdeploy
![](https://i.imgur.com/Y576D14.png)
    - The example above shows 1 compute-node with 2 test-VM and 1 server node
    
- Server-node should have java8 installed
```
## add repository to the apt-get
sudo add-apt-repository ppa:openjdk-r/ppa
sudo apt-get update
## install openjdk-8
sudo apt-get install openjdk-8-jdk
```
- Change the file `install-no-kvm.sh` in apm-kernel_4.15.0-55-generic/

- `sudo su` in root and  use `./amd11` to run the code 