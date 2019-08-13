# Recompile Kernel on Linux

## Prerequisite of Building the Kernel
-	Check gcc is installed 
-	Tools needed:
```
sudo apt-get install build-essential libncurses5-dev xz-utils libssl-dev kernel-package wget

```

## Step1.0 :到 Kernel.org 下載需要的版本 
- 用 git clone 或 wget 下載原始碼 並丟到 /usr/src 的資料夾下
``` 
wget https://github.com/torvalds/linux/archive/v4.x/linux-4.15.tar.gz 
tar zxvf linux-4.15.tar.gz
cd linux-4.15/
```
## Step1.1 :Ubuntu Launchpad the Sub-version of Kernel Source Code 
    Link:https://launchpad.net/ubuntu/+source/linux/4.15.0-50.54
- There are 3 files to be downloaded `linux_4.15.0.orig.tar.gz & linux_4.15.0-50.54.diff.gz & linux_4.15.0-50.54.dsc` 
    - .orig.tar.gz -> The original kernel
    - .diff.gz -> The diffence (patch) between the updated code and the original code.
    - .dsc -> A short textfile descripts of the .orig and .diff and connect the files above
![](https://i.imgur.com/RKficKz.png)
- Use the dpkg to extract the files
```
$ dpkg-source -x package.dsc
```
    

## Step2: 設定 config 來調整硬體需求
- 複製原有的 config 檔案，重新存成一份 .config 
- 可用xconfig,or menuconfig 來設定config檔
- Change the name of compile kernel version name:
`vim Makefile`
to change the version name as the photo below before compiling
![](https://i.imgur.com/jkzbdg2.png)



```
cp /boot/config-4.4.0-21-generic ./.config
make menuconfig
```

## Step3: Compile the kernel
-  -j 4 代表使用4核心進行編譯，可以加速 compile 的慢長過程

```
sudo make -j 4 clean
sudo make -j 4
sudo make modules -j 4
sudo make modules_install
sudo make install
```


## Step4: 更新initramfs image
```
 sudo update-initramfs -u -k all
```
## Step5: 更新grub-list
- 重開機後按 Esc 開機選單就可看到可選的新裝好的kernel開機
```
 sudo update-grub 
```

# Ubuntu package of Kernel (compiled)
```
sudo apt-get linux-header-4.15.0-55-generic
```






# Run the APM code on docker 
## Prerequisite
- docker installed
```
sudo apt install docker.io
```
## Build the 16.04 ubuntu docker image
- Go the directory of `docker/addm-build-ubuntu16` and run the build.sh file
```
cd docker/addm-build-ubuntu16
sh build.sh
```
- problem may encounter: `E:Unable to locate package ca-certificates The command '/bin/sh -c apt-get install -y ca-certificates' return a non-zero code:100`
- solution: Set the DNS server to ITRI Domain as below
![](https://i.imgur.com/bR11WkW.png)
## Run the image on docker and build the code
- `cd ..` to the docker directory and change the image source in `run-docker.sh` (ex:`u16.04`) and run the `run-docker.sh`  file
![](https://i.imgur.com/yDUyb8j.png)
- Problem may encounter: Permission denied of `XXX.sh` 
- Solution: Use command `chmod +x ./sh` to make the .sh file executable 

![](https://i.imgur.com/xq4HivY.png)

- After entering the container, go to the directory addm and run the `build.sh` file and the result will be as the photo below
```
cd addm
sh build.sh
```
![](https://i.imgur.com/4GdGLg3.png)

## The result file package.tar.gz
- After building the code we will get the `package.tar.gz`
- Move the `package.tar.gz` to the host by the command:
```
docker cp <containerId>:/file/path/within/container /host/path/target
```
![](https://i.imgur.com/ZY3MOhA.png)

## Change the file kvm.ko and kvm-intel.ko in the kernel modules
- untar the `package.tar.gz` we will get a **addm** directory
- The `kvm.ko and kvm-intel.ko`, built by us, are under the directory /addm/bin 
- Move these two files to the kernel module in the `/lib/module/4.15.0-50-generic/kernel/arch/x86/kvm`

![](https://i.imgur.com/bY7XVr1.png)

![](https://i.imgur.com/H9d9j0Y.png)
- Reboot to check whether they work