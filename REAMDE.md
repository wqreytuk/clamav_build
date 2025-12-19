跟着官方文档

https://docs.clamav.net/manual/Development/development-builds.html#building-for-development

前面这些步骤都是没有问题的


<img width="1032" height="768" alt="image" src="https://github.com/user-attachments/assets/5458575b-cec1-43ab-9f1c-06e9a2e2e815" />


然后安装mussels

<img width="964" height="634" alt="image" src="https://github.com/user-attachments/assets/43cb2715-2d68-4e37-b38c-2a0e5a77f896" />


在执行`msl build clamav_deps`的时候会遇到mv/cp/rm命令不存在的问题，需要我们手动编写3个对应名称bat脚本到`C:\windows`目录下

[mv.bat](https://github.com/wqreytuk/article/blob/main/mv.bat)
[rm.bat](https://github.com/wqreytuk/article/blob/main/rm.bat)
[cp.bat](https://github.com/wqreytuk/article/blob/main/cp.bat)

然后再执行`msl build clamav_deps`

之后我们需要到下载[rust安装程序rustup‑init.exe](https://rustup.rs/)安装rust，默认安装就行了，如果出现网速很慢的问题，就打开clash的这两个选项

<img width="424" height="286" alt="image" src="https://github.com/user-attachments/assets/cc5676dc-0e5c-4578-985a-8814098d627e" />

之后安装pytest

```
python -m pip install pytest
```

然后打开vs2017的x64 build命令行，`cd C:\users\x\clamav_main\build`，执行如下命令

```bat
cmake ..  -G Ninja -D CMAKE_BUILD_TYPE="Debug"   -D ENABLE_EXAMPLES=OFF                                                  -D JSONC_INCLUDE_DIR="C:\users\x\.mussels\install\x64\include\json-c"         -D JSONC_LIBRARY="C:\users\x\.mussels\install\x64\lib\json-c.lib"             -D ENABLE_JSON_SHARED=OFF                                               -D BZIP2_INCLUDE_DIR="C:\users\x\.mussels\install\x64\include"                -D BZIP2_LIBRARY_RELEASE="C:\users\x\.mussels\install\x64\lib\libbz2.lib"     -D CURL_INCLUDE_DIR="C:\users\x\.mussels\install\x64\include"                 -D CURL_LIBRARY="C:\users\x\.mussels\install\x64\lib\libcurl_imp.lib"         -D OPENSSL_ROOT_DIR="C:\users\x\.mussels\install\x64"                         -D OPENSSL_INCLUDE_DIR="C:\users\x\.mussels\install\x64\include"              -D OPENSSL_CRYPTO_LIBRARY="C:\users\x\.mussels\install\x64\lib\libcrypto.lib" -D ZLIB_LIBRARY="C:\users\x\.mussels\install\x64\lib\libssl.lib"              -D LIBXML2_INCLUDE_DIR="C:\users\x\.mussels\install\x64\include\libxml2"      -D LIBXML2_LIBRARY="C:\users\x\.mussels\install\x64\lib\libxml2.lib"          -D PCRE2_INCLUDE_DIR="C:\users\x\.mussels\install\x64\include"                -D PCRE2_LIBRARY="C:\users\x\.mussels\install\x64\lib\pcre2-8.lib"            -D CURSES_INCLUDE_DIR="C:\users\x\.mussels\install\x64\include"               -D CURSES_LIBRARY="C:\users\x\.mussels\install\x64\lib\pdcurses.lib"          -D PThreadW32_INCLUDE_DIR="C:\users\x\.mussels\install\x64\include"           -D PThreadW32_LIBRARY="C:\users\x\.mussels\install\x64\lib\pthreadVC3.lib"    -D ZLIB_INCLUDE_DIR="C:\users\x\.mussels\install\x64\include"                 -D ZLIB_LIBRARY="C:\users\x\.mussels\install\x64\lib\zlibstatic.lib"          -D LIBCHECK_INCLUDE_DIR="C:\users\x\.mussels\install\x64\include"             -D LIBCHECK_LIBRARY="C:\users\x\.mussels\install\x64\lib\checkDynamic.lib"    -D CMAKE_INSTALL_PREFIX="install"
```

即可
