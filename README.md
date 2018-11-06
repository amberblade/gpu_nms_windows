# gpu_nms_windows
python gpu_nms modules for windows

In VS 2015, Please use the X64 Prompt or use "VS2015 x86 x64 Cross Tools Command Prompt"

When encount the error: 
```console
gpu_nms.cpp(2147): error C2664: 'void _nms(int *,int *,const float *,int,int,float,int)': cannot convert argument 1 from '__pyx_t_5numpy_int32_t *' to 'int *'
```

Change the generated file gpu_nms.cpp:
```C++
_nms((&(*__Pyx_BufPtrStrided1d(__pyx_t_5numpy_int32_t *, __pyx_pybuffernd_keep.rcbuffer->pybuffer.buf, __pyx_t_10, __pyx_pybuffernd_keep.diminfo[0].strides))), (&__pyx_v_num_out), (&(*__Pyx_BufPtrStrided2d(__pyx_t_5numpy_float32_t *, __pyx_pybuffernd_sorted_dets.rcbuffer->pybuffer.buf, __pyx_t_12, __pyx_pybuffernd_sorted_dets.diminfo[0].strides, __pyx_t_13, __pyx_pybuffernd_sorted_dets.diminfo[1].strides))), __pyx_v_boxes_num, __pyx_v_boxes_dim, __pyx_t_14, __pyx_v_device_id);
```

to 

```C++
_nms((&(*__Pyx_BufPtrStrided1d(int *, __pyx_pybuffernd_keep.rcbuffer->pybuffer.buf, __pyx_t_10, __pyx_pybuffernd_keep.diminfo[0].strides))), (&__pyx_v_num_out), (&(*__Pyx_BufPtrStrided2d(__pyx_t_5numpy_float32_t *, __pyx_pybuffernd_sorted_dets.rcbuffer->pybuffer.buf, __pyx_t_12, __pyx_pybuffernd_sorted_dets.diminfo[0].strides, __pyx_t_13, __pyx_pybuffernd_sorted_dets.diminfo[1].strides))), __pyx_v_boxes_num, __pyx_v_boxes_dim, __pyx_t_14, __pyx_v_device_id);
```
