# How a open gles program run on Linux
## Mesa create context
1. In libglut.so.3 will call glutCreateWindow
2. fgCreateWindow
3. fgOpenWindow
4. call glxcmds.c：：glXCreateNewContext
5. call glxcmds.c：：CreateContext
6. dri_common.c：：dri_common_create_context
7. drisw_glx.c：：drisw_create_context_attribs
8. dri_util.c：：driCreateContextAttribs
9. dri_context.c：：dri_create_context
10. st_manager.c：：st_api_create_context
11. context.c：：_mesa_initialize
## Load library
1. call dlopen  to load necessary lib:libGL.so.1, libGL.so, if success, call dlsym to find glXGetProcAddressARB address.
2. when need to use a gl function，load-->get_proc-->glXGetProcAddressARB(glname) to get function address。
3. glXGetProcAddressARB call glxcmds.cpp::get_glx_proc_address(name) to find func addr in function table[name] 
4. glXGetProcAddressARB call mapi_glapi.c：：_glapi_get_proc_address-->_glapi_get_stub-->stub_find_public
5. call func_name()
