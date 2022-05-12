# How a open gles program run
## Load library
1. call dlopen  to load necessary lib:libGL.so.1, libGL.so, if success, call dlsym to find glXGetProcAddressARB address.
2. when need to use a gl function，call glXGetProcAddressARB(glname) to get function address。
3. glXGetProcAddressARB call glxcmds.cpp::get_glx_proc_address(name) to find func addr in function table[name] 
4. glXGetProcAddressARB call mapi_glapi.c：：_glapi_get_proc_address-->_glapi_get_stub-->stub_find_public
5. call func_name()
