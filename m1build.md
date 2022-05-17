# m1上编译mesa

m1上编译mesa有两种方式：
1. 编译arm64版本
2. 编译x86_64版本
这两种的编译配置文件稍微有所不同。
## 编译arm64
配置zsh，保证运行的是arm版本的brew
export PATH=/opt/homebrew/bin:$PATH
保证找到arm版本的lib
export LD_LIBRARY_PATH=/opt/homebrew/lib
然后安装x11，xext等arm64版本的包到/opt/homebrew下面。
配置完成后生成的build.ninja里面链接的库都是/opt/homebrew下面的arm64版本

## 编译选项
因为需要使用mesa提供的opengl，所以要打开软件渲染器，同时打开asahi提供的driver和compiler
meson_option：
gallium_driver：asahi, swrast
glx：gallium-xlib



## 编译x86_64
配置zsh，保证运行的是x86版本的brew
export PATH=/usr/local/bin：$PATH
保证找到x86的lib
export LD_LIBRARY_PATH=/usr/local/lib
然后安装x11，xext等x86版本包到/usr/local下面。
编译的命令需要加上arch x86_64 meson ..。
