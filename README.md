# How a open gles program run
## Load library
1. call dlopen  to load necessary lib:libGL.so.1, libGL.so, if success, call dlsym to find glXGetProcAddressARB address.
2. 
