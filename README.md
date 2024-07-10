# 负载均衡式在线OJ

## 1. 演示项目





## 2. 所用技术与开发环境

**所用技术：**

- `C++ STL` 标准库
- `Boost` 准标准库(字符串切割)
- `cpp-httplib` 第三方开源网络库
- `ctemplate` 第三方开源前端网页渲染库
- `jsoncpp` 第三方开源序列化、反序列化库
- 负载均衡设计
- 多进程、多线程
- `MySQL C connect`
- Ace前端在线编辑器(了解)
- `html/css/js/jquery/ajax`(了解)

**开发环境**

- `Centos 7` 云服务器
- `vscode`



## 3. 项目宏观结构

**I. `leetcode` 结构**

**II. 我们的项目宏观结构**

**III. 编写思路**



## 4. `compiler` 服务设计



## 5. 基于 `MVC` 结构 `oj` 服务设计



## 6. `version1` 文件版题目设计



## 7. 前端页面设计



## 8. `version2` MySQL版题目设计



## 9. 综合测试



## 10. 项目扩展思路(学有余力)



## **备注**

`升级 gcc`

```c
$ gcc -v
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/libexec/gcc/x86_64-redhat-linux/4.8.5/lto-wrapper
Target: x86_64-redhat-linux
Configured with: ../configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --with-bugurl=http://bugzilla.redhat.com/bugzilla --enable-bootstrap --enable-shared --enable-threads=posix --enable-checking=release --with-system-zlib --enable-__cxa_atexit --disable-libunwind-exceptions --enable-gnu-unique-object --enable-linker-build-id --with-linker-hash-style=gnu --enable-languages=c,c++,objc,obj-c++,java,fortran,ada,go,lto --enable-plugin --enable-initfini-array --disable-libgcj --with-isl=/builddir/build/BUILD/gcc-4.8.5-20150702/obj-x86_64-redhat-linux/isl-install --with-cloog=/builddir/build/BUILD/gcc-4.8.5-20150702/obj-x86_64-redhat-linux/cloog-install --enable-gnu-indirect-function --with-tune=generic --with-arch_32=x86-64 --build=x86_64-redhat-linux
Thread model: posix
gcc version 4.8.5 20150623 (Red Hat 4.8.5-44) (GCC)
    
cpp-httplib 用老的编译器，要么编译不通过，要么直接运行报错
    
百度搜索: scl gcc devsettool升级gcc
    
//安装scl
$ sudo yum install centos-release-scl scl-utils-build
//安装新版本gcc，这里也可以把7换成8或者9，我用的是9，也可以都安装
$ sudo yum install -y devtoolset-7-gcc devtoolset-7-gcc-c++    
$ ls /opt/rh/
    
//启动：细节，命令行启动只能在本会话有效
$ scl enable devtoolset-7 bash
$ gcc -v
    
//可选：如果想每次登录的时候，都是较新的gcc，需要把上面的命令添加到你的~/.bash_profile中
$ cat ~/.bash_profile
# .bash_profile

# Get the aliases and functions
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# User specific environment and startup programs

PATH=$PATH:$HOME/.local/bin:$HOME/bin

export PATH

#添加下面的命令，每次启动的时候，都会执行这个scl命令
scl enable devtoolset-7 bash  
    
or
    
scl enable devtoolset-8 bash 
    
or
    
scl enable devtoolset-9 bash     
```



`安装 jsoncpp`

```c
$ sudo yum install -y jsoncpp-devel
Loaded plugins: auto-update-debuginfo, fastestmirror, langpacks
Repository epel is listed more than once in the configuration
Loading mirror speeds from cached hostfile
 * centos-sclo-rh: mirrors.aliyun.com
 * centos-sclo-sclo: mirrors.aliyun.com
 * epel-debuginfo: mirrors.aliyun.com
Package jsoncpp-devel-0.10.5-2.el7.x86_64 already installed and latest version
//我已经安装了
```



`安装 cpp-httplib`

```c
最新的cpp-httplib在使用的时候，如果gcc不是特别新的话有可能会有运行时错误的问题
    
建议: cpp-httplib 0.7.15
    
下载zip安装包，上传到服务器即可
    
cpp-httplib gitee链接: https://gitee.com/yuanfeng1897/cpp-httplib?_from=gitee_search
v0.7.15版本链接: https://gitee.com/yuanfeng1897/cpp-httplib/tree/v0.7.15

把httplib.h拷贝到我们的项目中即可，就这么简单

使用样例:

$ cat http_server.cc 
```

