# 运行命令

编译好mesa后，运行opengl程序：  DYLD_SEARCH_PATH=./galliux-xlib ./XXX

# 流程
1. 程序中call glutCreateWindow
2. 调用glut中对应的函数：
  fgCreateWindow
  fgOpenWindow
  fghChooseConfig
3. 从glut调用到libGL中的函数
  glx_api.c::glxChooseFBConfig<BR>  choose_visual<BR>  xmesa_init <BR> xmesa_init_display<BR>  swrast_xlib_create_screen(inline_sw_helper.h:114-->80) <BR>
  agx_screen_create<BR> agx_open_device<BR>
  
