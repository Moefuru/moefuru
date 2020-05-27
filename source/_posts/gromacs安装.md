---
title: gromacs安装
date: 2020-05-27 14:45:55
tags:
---

### gromacs的官网

http://gromacs.org

### 官方的安装文档

{% blockquote http://manual.gromacs.org/documentation/current/install-guide/index.html %}
tar xfz gromacs-2020.2.tar.gz
cd gromacs-2020.2
mkdir build
cd build
cmake .. -DGMX_BUILD_OWN_FFTW=ON -DREGRESSIONTEST_DOWNLOAD=ON
make
make check
sudo make install
source /usr/local/gromacs/bin/GMXRC
{% endblockquote %}


### 开始安装

一般情况下按照官方执行上面的命令即可完成安装，但是由于种种原因，安装起来并不理想
cmake .. -DGMX_BUILD_OWN_FFTW=ON  DGMX_BUILD_OWN_FFTW 参数设置为ON时将自动下载FFTW（国内下载较慢建议手动安装）
有关FFTW安装的更多信息可以转到 https://blog.mrzhenggang.com/fftw-install/
FFTW下载地址：http://www.fftw.org/download.html
安装FFTW：

```
tar zxvf fftw-3.3.8.tar.gz  
cd fftw-3.3.8 
./configure  
make  
make install
```

接下来我们就可以开始安装gromacs

```
tar xfz gromacs-2020.2.tar.gz
cd gromacs-2020.2
mkdir build
cd build
指定FFTW的安装位置 export CMAKE_PREFIX_PATH=FFTW3的安装目录（安装时没有指定路径，默认在/usr/lcoal下）
export CMAKE_PREFIX_PATH=/usr/lcoal/fftw
cmake .. -DGMX_GPU=ON (-DGMX_GPU=ON 启用GPU支持 如果没有GPU 则执行 cmake .. 即可)
make
make check
sudo make install
```

### 安装完成

```
将gromacs加入环境变量
修改~/.bashrc在=最后一行添加 export PATH="$PATH:/usr/local/gromacs/bin"
执行 source ~/.bashrc
执行 gmx --version 输出gromacs的信息即为安装成功
```