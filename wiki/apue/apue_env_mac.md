* 解包src.tar.gz
* 打开path_to_apue_src/Make.defines.macos，修改WKDIR的路径为apue.2e的绝对路径，如：

        WKDIR=/Users/venj/Developer/Sources/C/APUE/apue #也就是path_to_apue_src
* 打开path_to_apue_src/include/apue.h，在第11行之后加入如下几行：

        #ifdef MACOS
        #define _DARWIN_C_SOURCE
        #endif

* 打开终端，cd到path_to_apue_src/include/apue.h目录，运行：

        make all

* 编译源码的方法如下：

        gcc -Ipath_to_apue_src/include path_to_apue_src/lib/libapue.a example.c -o exec_file 
