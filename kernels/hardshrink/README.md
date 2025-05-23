# HardSharink

## 0x00 说明

包含以下内容：

- [X] hardshrink_f32_kernel
- [X] hardshrink_f32x4_kernel(float4向量化版本)
- [X] hardshrink_f16_kernel(fp16版本)
- [X] hardshrink_f16x2_kernel(fp16向量化版本)
- [X] hardshrink_f16x8_kernel(fp16向量化版本)
- [X] hardshrink_f16x8_pack_kernel(fp16向量化，pack版本)
- [X] PyTorch bindings


## 测试

```bash
# 只测试Ada架构 不指定默认编译所有架构 耗时较长: Volta, Ampere, Ada, Hopper, ...
export TORCH_CUDA_ARCH_LIST=Ada
python3 hardshrink.py
```

输出:

```bash
-------------------------------------------------------------------------------------
                                        S=1024, K=1024
           out_f32: ['0.0         ', '0.0         '], time:0.00428367ms
         out_f32x4: ['0.0         ', '0.0         '], time:0.00370097ms
        out_f32_th: ['0.0         ', '0.0         '], time:0.00739479ms
-------------------------------------------------------------------------------------
           out_f16: ['0.0         ', '0.0         '], time:0.00417209ms
         out_f16x2: ['0.0         ', '0.0         '], time:0.00280690ms
         out_f16x8: ['0.0         ', '0.0         '], time:0.00266337ms
     out_f16x8pack: ['0.0         ', '0.0         '], time:0.00255847ms
        out_f16_th: ['0.0         ', '0.0         '], time:0.00636697ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=1024, K=2048
           out_f32: ['-0.82629085 ', '0.0         '], time:0.00588202ms
         out_f32x4: ['-0.82629085 ', '0.0         '], time:0.00565958ms
        out_f32_th: ['-0.82629085 ', '0.0         '], time:0.01137996ms
-------------------------------------------------------------------------------------
           out_f16: ['-0.82617188 ', '0.0         '], time:0.00589466ms
         out_f16x2: ['-0.82617188 ', '0.0         '], time:0.00484967ms
         out_f16x8: ['-0.82617188 ', '0.0         '], time:0.00404549ms
     out_f16x8pack: ['-0.82617188 ', '0.0         '], time:0.00391698ms
        out_f16_th: ['-0.82617188 ', '0.0         '], time:0.00740528ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=1024, K=4096
           out_f32: ['0.0         ', '0.0         '], time:0.01001120ms
         out_f32x4: ['0.0         ', '0.0         '], time:0.00953746ms
        out_f32_th: ['0.0         ', '0.0         '], time:0.01943731ms
-------------------------------------------------------------------------------------
           out_f16: ['0.0         ', '0.0         '], time:0.01005745ms
         out_f16x2: ['0.0         ', '0.0         '], time:0.00977778ms
         out_f16x8: ['0.0         ', '0.0         '], time:0.00651360ms
     out_f16x8pack: ['0.0         ', '0.0         '], time:0.00592923ms
        out_f16_th: ['0.0         ', '0.0         '], time:0.01157641ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=2048, K=1024
           out_f32: ['0.90714514  ', '0.0         '], time:0.00693989ms
         out_f32x4: ['0.90714514  ', '0.0         '], time:0.00567746ms
        out_f32_th: ['0.90714514  ', '0.0         '], time:0.01138806ms
-------------------------------------------------------------------------------------
           out_f16: ['0.90722656  ', '0.0         '], time:0.00694394ms
         out_f16x2: ['0.90722656  ', '0.0         '], time:0.00400567ms
         out_f16x8: ['0.90722656  ', '0.0         '], time:0.00397611ms
     out_f16x8pack: ['0.90722656  ', '0.0         '], time:0.00391245ms
        out_f16_th: ['0.90722656  ', '0.0         '], time:0.00740814ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=2048, K=2048
           out_f32: ['-0.61146295 ', '-1.60048997 '], time:0.01001549ms
         out_f32x4: ['-0.61146295 ', '-1.60048997 '], time:0.00960755ms
        out_f32_th: ['-0.61146295 ', '-1.60048997 '], time:0.01942730ms
-------------------------------------------------------------------------------------
           out_f16: ['-0.61132812 ', '-1.60058594 '], time:0.01005864ms
         out_f16x2: ['-0.61132812 ', '-1.60058594 '], time:0.00810075ms
         out_f16x8: ['-0.61132812 ', '-1.60058594 '], time:0.00622988ms
     out_f16x8pack: ['-0.61132812 ', '-1.60058594 '], time:0.00591063ms
        out_f16_th: ['-0.61132812 ', '-1.60058594 '], time:0.01156282ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=2048, K=4096
           out_f32: ['0.0         ', '0.55151719  '], time:0.01828051ms
         out_f32x4: ['0.0         ', '0.55151719  '], time:0.01861715ms
        out_f32_th: ['0.0         ', '0.55151719  '], time:0.09329295ms
-------------------------------------------------------------------------------------
           out_f16: ['0.0         ', '0.55175781  '], time:0.01676941ms
         out_f16x2: ['0.0         ', '0.55175781  '], time:0.01659012ms
         out_f16x8: ['0.0         ', '0.55175781  '], time:0.00997281ms
     out_f16x8pack: ['0.0         ', '0.55175781  '], time:0.00901723ms
        out_f16_th: ['0.0         ', '0.55175781  '], time:0.01817441ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=4096, K=1024
           out_f32: ['1.19508219  ', '0.75319326  '], time:0.01123738ms
         out_f32x4: ['1.19508219  ', '0.75319326  '], time:0.00885844ms
        out_f32_th: ['1.19508219  ', '0.75319326  '], time:0.01797009ms
-------------------------------------------------------------------------------------
           out_f16: ['1.1953125   ', '0.75341797  '], time:0.01144171ms
         out_f16x2: ['1.1953125   ', '0.75341797  '], time:0.00580645ms
         out_f16x8: ['1.1953125   ', '0.75341797  '], time:0.00570226ms
     out_f16x8pack: ['1.1953125   ', '0.75341797  '], time:0.00586438ms
        out_f16_th: ['1.1953125   ', '0.75341797  '], time:0.01156831ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=4096, K=2048
           out_f32: ['0.58269709  ', '-0.82688355 '], time:0.01827741ms
         out_f32x4: ['0.58269709  ', '-0.82688355 '], time:0.01818061ms
        out_f32_th: ['0.58269709  ', '-0.82688355 '], time:0.09307647ms
-------------------------------------------------------------------------------------
           out_f16: ['0.58251953  ', '-0.82666016 '], time:0.01676655ms
         out_f16x2: ['0.58251953  ', '-0.82666016 '], time:0.01336956ms
         out_f16x8: ['0.58251953  ', '-0.82666016 '], time:0.00968409ms
     out_f16x8pack: ['0.58251953  ', '-0.82666016 '], time:0.00905466ms
        out_f16_th: ['0.58251953  ', '-0.82666016 '], time:0.01817107ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=4096, K=4096
           out_f32: ['0.0         ', '0.0         '], time:0.14530301ms
         out_f32x4: ['0.0         ', '0.0         '], time:0.14572287ms
        out_f32_th: ['0.0         ', '0.0         '], time:0.29304075ms
-------------------------------------------------------------------------------------
           out_f16: ['0.0         ', '0.0         '], time:0.03192568ms
         out_f16x2: ['0.0         ', '0.0         '], time:0.03173161ms
         out_f16x8: ['0.0         ', '0.0         '], time:0.01897788ms
     out_f16x8pack: ['0.0         ', '0.0         '], time:0.01702213ms
        out_f16_th: ['0.0         ', '0.0         '], time:0.09349132ms
-------------------------------------------------------------------------------------

```
