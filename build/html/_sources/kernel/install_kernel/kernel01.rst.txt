.. _kernel01:

=============
Debian编译安装内核
=============


下载内核源码包
===============


::
    
    https://kernel.org/

下载需要的源码包即可


清理目录
===============
:: 

    make mrproper
    make clean
    make distclean    

修改配置文件
===============
复制/boot/config-xxx文件到源码目录

.. code:: bash

    cp /boot/config-5.10.0-8-amd64 ~/kernel/linux-source-5.10/.config 

执行 ``make oldconfig`` 或 ``make menuconfig``
根据提示安装需要的包， ``如flex,bison`` 等，直到执行成功。
使用其他 (通常是较旧的) 内核版本的 .config 文件时，需要先更新它。

.. tip:: 


.. admonition:: 处理过时的 .config 文件

    使用其他 (通常是较旧的) 内核版本的 .config 文件时，需要先更新它。
    可以使用 make oldconfig 命令，以交互方式询问对新配置的选择。可以用 make olddefconfig 命令使用问题缺省的答案。
    以 make oldnoconfig 命令，可以对问题提供缺省的答案。

开始编译
===============
使用 ``使用make deb-pkg`` 编译内核deb包（需要先执行 ``apt-get install dpkg-dev bc rsync`` ）