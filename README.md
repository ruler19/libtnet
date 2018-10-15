# Introduction

libtnet is a tiny high performance network lib, purpose is to simplify the network programming.

# Install

go to root source, then

    mkdir -p build
    cd build
    cmake ..
    make
    make install

# Requirement

- gcc >= 4.4, supports c++ 0x
- linux, supports eventfd, signalfd and timerfd 

# Not supported!

- unix socket domain
- ssl

# Other

please see [wiki](https://github.com/siddontang/libtnet/wiki) for more information. If you have any problem when using libtnet, you can contact me through below.

- Gmail: siddontang@gmail.com
- Twitter: siddontang

I thank you very much for your feedback!

//-------------------------------------------------------------
https://blog.csdn.net/guowenyan001/article/details/9358665
libnet编译，windows/Linux

windows下

1.下载安装包libnet-libnet-1.2-rc2.zip

https://github.com/sam-github/libnet/releases

2.解压缩到D:\libnet-libnet-1.2-rc2目录下

3.下载WinPcap_4_1_2.zip和WpdPack_4_1_2.zip
    安装WinPcap_4_1_2
    解压WpdPack_4_1_2.zip解压到D:\WpdPack

4.编译

   3.1 打开VS -> Visual Studio Tools -> Visual Studio 命令提示(2010)

   3.2 切换到目录D:\libnet-libnet-1.2-rc2\libnet

   3.3 执行msvcbuild.bat

   3.4 其他

       a. 提示找不到“pcap.h”。 

           修改msvcbuild.bat中的“@set WINPCAP=..\..\..\WpdPack”为“@set WINPCAP=D:\WpdPack”

       b. libnet_dll.c(32) : fatal error C1083: 无法打开包括文件:“common”: No such file or directory

          将libnet_dll.c中32行的 #include "common" 改成 #include "common.h" 。

      c.  libnet_raw.c(44) : error C2054: 在“socklen_t”之后应输入“(”
           libnet_raw.c(45) : error C2082: 形参“libnet_open_raw4”的重定义
           libnet_raw.c(45) : error C2143: 语法错误 : 缺少“;”(在“{”的前面)

          将libnet_raw.c中35~37行的内容注释掉：

              #ifndef HAVE_SOCKLEN_T
              typedef int socklen_t
              #endif

          将libnet_raw.c中70行的 socklen_t len; 改成 int len; 。



5.生成结果

    在目录D:\libnet-libnet-1.2-rc2\libnet\src下生成libnet.lib、libnet.dll。



Linux下
1.下载安装包libnet-1.2-rc2.tar.gz 

http://sourceforge.net/projects/libnet-dev/ 

2.解压缩libnet-1.2-rc2.tar.gz 
   tar zxvf libnet-1.2-rc2.tar.gz

3.编译
  3.1 ./configure
  3.2 make
  3.3 make install

4.生成结果
   在libnet-1.2-rc2/src/.libs/目录下生成libnet.a、libnet.so。
