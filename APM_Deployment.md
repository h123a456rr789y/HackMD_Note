---
title: APM Deployment
tags: Intern, APM
description:
---


# APM Deployment
## APM structure
### Haas Machine 
![](https://i.imgur.com/9NWG5gj.jpg)
### Machine in 78 Lab
![](https://i.imgur.com/df8snkD.jpg)




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

## Passwordless for Root
- Edit the file /etc/sudoers
```
sudo vim /etc/sudoers

##Add the line in the this file 

username  ALL=(ALL) NOPASSWD: ALL

```



## Setup Passwordless with ssh
- Set up passwordless connection between (CN&SN),(SN & TestVM) and (DN & CN) bidirectionally

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
    - test <-> test
    - test <-> root
    - root <-> test
    - root <-> root
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
![](https://i.imgur.com/I2OeBJl.png)
    - The vm name must be the same as it in your kvm
    
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



## Set /etc/hosts
- Add «addm»(server node ip) to /etc/hosts on both compute node and server side e.g.: 192.168.100.90 addm
- add compute node to /etc/hosts with the same name as in _amnodspec.yaml on server node e.g.: 192.168.100.91 addmcompute1

![](https://i.imgur.com/wvYfXxP.png)

![](https://i.imgur.com/j2wUsN8.png)




## testing if APM is working correctly:
1. Make sure mac and ip address of the VM on the compute node is correct
2. Install apache webserver on the VM (sudo apt-get install apache2)
3. On the compute node run /opt/addm/bin/start-agent
4. On the server node run /opt/addm/bin/start-server
5. On the server node in a separate terminal run /opt/addm/bin/cli enable 1
6. Issue http request to the vm (e.g. curl VM_IP). This has to be done from any host except Compute Node, otherwise it will not be trapped.




## Web Server Deployment
### Environment and Prerequisite
- Ubuntu 14.04
- Install JDK7
```bash=
sudo add-apt-repository ppa:openjdk-r/ppa  
sudo apt-get update   
sudo apt-get install openjdk-7-jdk  
```
- Install MySQL 
    - 安裝過程會要你輸入root帳號的密碼
```bash=
sudo apt-get install mysql-server
```
- MySQL Setting
    - Enter MySQL
    ```
     shell> mysql
    ```
    - Create DB
    ```
    mysql> create database apmdb;
    ```
    - Import DB
    ```
     shell> mysql -u root -p apmdb < /home/test/iii/apm-kernel_4.15.0-55-generic/addmui/DBSchema/apm_v0.1.sql
    ```
    - Add one 'MySQL' user “username = test, password = test”
    ```mysql
     mysql> create user 'test'@'%' identified by 'test';
     mysql> grant all privileges on *.* to 'test'@'%' with grant option;
    ```
    - Edit /etc/mysql/mysql.conf.d/mysqld.cnf
    ```
    replace: from bind-address = 127.0.0.1
               to bind-address = 0.0.0.0

    ```
    - Restart MySQL service 
    ```
    shell> service mysql restart
    ```
    
- Install Glassfish
    1. 官網下載glassfish.zip 
    2. mysql-connector-java-5.1.35-bin.jar，把它copy到glassfish3/glassfish/lib/ 裡面
    3. 改glassfish 管理員密碼，預設帳號為 admin，因尚未設定密碼，在提示Enter admin password> 時，請直接按下enter鍵，接下來再設定新的密碼。 
    4. 啟動glassfish
    5. 設定允許遠端安全管理，啟動glassfish後，執行以下指令，並重啟glassfish
```bash=
#1
wget http://download.java.net/glassfish/3.1.2.2/release/glassfish-3.1.2.2.zip
unzip glassfish-3.1.2.2.zip
#2
cp ~/mysql-connector-java-5.1.35/mysql-connector-java-5.1.35-bin.jar ~/glassfish3/glassfish/lib/
#3
~/glassfish3/bin/asadmin change-admin-password
#4
cd ~/glassfish3/bin
./asadmin start-domain
#5
./asadmin --host localhost --port 4848 enable-secure-admin
./asadmin restart-domain
```

- 設定SQL DB Connection Pool
- Glassfish啟動後，打開瀏覽器連到https://localhost:4848
![](https://i.imgur.com/2Rr40SZ.png)
    - 點選JDBC
    - 點選JDBC Connection Pools
    - 點選New…
    - Pool Name可以隨便你取，建議有APM字眼方便自己識別，如APMPool。
Resource Type點選javax.sql.DataSource。
Database Driver Vendor點選MySQL。
輸入完後點”Next”按鈕。
![](https://i.imgur.com/UbT9x83.png)
    -  向下捲動可看到Additional Properties列表
    輸入欄位如下所示
表 3: 新增acs JDBC Connection Pool Step2 Additional Properties輸入欄位


| Property     | Value | 備註 |
| --------     | -------- | -------- |
| User       | root    |    |
|ServerName	 |  localhost    | 要連到的MySQL server的hostname，安裝在同一台填localhost|
|    DatabaseName     |    apmdb	    |        |
|  Password          |       password	     |      請輸入當初安裝MySQL時所設定的root的密碼          |
	
- 再來勾選Url跟URL後點”Delete Properties”按鈕。額外再設一個欄位Encoding，設為UTF8。最後捲到最上面，點”Finish”按鈕，完成新增專案的JDBC Connection Pool。
![](https://i.imgur.com/qgdRnqD.png)
- 完成後，可以點擊上圖列表的Connection Pool的超連結，進到修改畫面，可點擊“Ping”按鈕，確定是否設定正確、能成功連線。在點擊“Ping”按鈕之前請先按照2.2.9之步驟進行SQL檔案匯入以建立資料庫表單。
![](https://i.imgur.com/bVhdIsw.png)

- 新增JDBC Resources
    - 點JDBC Resources
    - 點New…
    ![](https://i.imgur.com/bQC4wcP.png)
    - JNDI Name填APMDatabase，Pool Name點選APMPool，點”OK”按鈕即可完成新增APM的JDBC Resources。
    - 可以看到APMDatabase已新增到JDBC Resources列表了。
    ![](https://i.imgur.com/6QMuKDH.png)
