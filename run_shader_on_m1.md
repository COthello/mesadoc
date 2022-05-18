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
  
 # 编译shader
  opengl调用glCompileShader之后先进行parse，生成ast tree之后，调用glLinkProgram才会去真正生成IR，调用后端编译器生成指令。
  1. glClear
  2. _mesa_clear
  3. _mesa_update_state
  4. _mesa_update_state_locked
  5. update_program
  6. _mesa_get_fixed_func_fragment_program
  7. create_new_program
  8. _mesa_glsl_link_shader
  9. st_link_shader
  
