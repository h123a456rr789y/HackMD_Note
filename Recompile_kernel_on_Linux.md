# Recompile Kernel on Linux

## Step1: 到 Kernel.org 下載需要的版本
- 用 git clone 或 wget 下載原始碼 並丟到 /usr/src 的資料夾下
``` 
wget https://github.com/torvalds/linux/archive/v4.x/linux-4.15.tar.gz 
tar zxvf linux-4.15.tar.gz
cd linux-4.15/
```
## Step2: 設定 config 來調整硬體需求
- 複製原有的 config 檔案，重新存成一份 .config 
- 可用xconfig,or menuconfig 來設定config檔
    - 可能會遇到manuconfig 開不起來的情況 ncurses not installed error: ncurses是在terminal提供了類GUI的接口
    用`sudo apt-get install libncurses5-dev`來安裝
```
cp /boot/config-4.4.0-21-generic ./.config
make menuconfig
```

## Step3: Compile the kernel
-  -j 4 代表使用4核心進行編譯，可以加速 compile 的漫長過程
-  The packages required before compiling the code: OpenSSL
    -  `sudo apt-get install libssl-dev`
    -  `sudo apt-get install libelf-dev`
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

# Ubuntu Launchpad the Sub-version of Kernel Source Code 
    Link:https://launchpad.net/ubuntu/+source/linux/4.15.0-50.54
- .orig.tar.gz -> The original kernel
- .diff.gz -> The diffence (patch) between the updated code and the original code.
- .dsc -> A short textfile descripts of the .orig and .diff and connect the files above

## Use the dpkg to extract the files
```
$ dpkg-source -x package.dsc
```
# Ubuntu package of Kernel (compiled)
```
sudo apt-get linux-header-4.15.0-55-generic
```