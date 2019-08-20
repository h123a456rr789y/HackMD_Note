---
title: Run the APM code on docker
tags: Intern, APM
description: building the apm code
---

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
bash build.sh
```
- Problem may encounter: `E:Unable to locate package ca-certificates The command '/bin/sh -c apt-get install -y ca-certificates' return a non-zero code:100`
- Solution: Set the DNS server to ITRI Domain as below
- This problem may also happened in docker container later, be sure to change the nameserver
![](https://i.imgur.com/bR11WkW.png)
## Run the image on docker and build the code
- `cd ..` to the docker directory and change the image source in `run-docker.sh` (ex:`u16.04`) and run the `run-docker.sh`  file with bash 
```
bash run-docker.sh
```
![](https://i.imgur.com/DjEz9XH.png)

- Problem may encounter: Permission denied of `XXX.sh` 
- Solution: Use command `chmod +x ./sh` to make the .sh file executable 

![](https://i.imgur.com/xq4HivY.png)

- After entering the container, go to the directory addm and run the `build.sh` file and the result will be as the photo below
```
cd addm
bash build.sh
```
![](https://i.imgur.com/4GdGLg3.png)

## The result file package.tar.gz
- After building the code, we will get a `package.tar.gz` file which will be located on the addm-master directory on the host as the photo shows
![](https://i.imgur.com/lrMS34n.png)


## Change the file kvm.ko and kvm-intel.ko in the kernel modules
- untar the `package.tar.gz` we will get a **addm** directory
- The `kvm.ko and kvm-intel.ko`, built by us, are under the directory /addm/bin 
- Move these two files to the kernel module in the `/lib/module/4.15.0-50-generic/kernel/arch/x86/kvm`

![](https://i.imgur.com/bY7XVr1.png)

![](https://i.imgur.com/DD7pwT1.png)

- Reboot to check whether the system function well
- Run and test at least one VM on the host to check the KVM modules are working. 
![](https://i.imgur.com/2HwpNV1.png)
