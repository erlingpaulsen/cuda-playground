# cuda-playground

# Useful commands
Query device information:
```bash
/usr/local/cuda-12.4/extras/demo_suite/deviceQuery
```

Compiling CUDA C++ files (with .cu extension):
```bash
nvcc array_addition_gpu.cu -o array_addition_gpu
```

Profiling a CUDA application
```bash
ncu array_addition_gpu
```
# Results
array_addition_gpu
```
add(int, float *, float *) (1, 1, 1)x(1, 1, 1), Context 1, Stream 7, Device 0, CC 8.6
    Section: GPU Speed Of Light Throughput
    ----------------------- ------------- ------------
    Metric Name               Metric Unit Metric Value
    ----------------------- ------------- ------------
    DRAM Frequency          cycle/nsecond         7.29
    SM Frequency            cycle/nsecond         1.41
    Elapsed Cycles                  cycle    809887455
    Memory Throughput                   %         1.71
    DRAM Throughput                     %         1.71
    Duration                      msecond       574.81
    L1/TEX Cache Throughput             %         0.78
    L2 Cache Throughput                 %         0.89
    SM Active Cycles                cycle  21227963.63
    Compute (SM) Throughput             %         0.02
    ----------------------- ------------- ------------
```
array_addition_gpu_parallel
```
add(int, float *, float *) (1, 1, 1)x(256, 1, 1), Context 1, Stream 7, Device 0, CC 8.6
    Section: GPU Speed Of Light Throughput
    ----------------------- ------------- ------------
    Metric Name               Metric Unit Metric Value
    ----------------------- ------------- ------------
    DRAM Frequency          cycle/nsecond         7.29
    SM Frequency            cycle/nsecond         1.41
    Elapsed Cycles                  cycle      5534390
    Memory Throughput                   %         1.82
    DRAM Throughput                     %         1.82
    Duration                      msecond         3.93
    L1/TEX Cache Throughput             %         4.77
    L2 Cache Throughput                 %         1.36
    SM Active Cycles                cycle    144739.32
    Compute (SM) Throughput             %         0.09
    ----------------------- ------------- ------------
```
array_addition_gpu_optimized
```
add(int, float *, float *) (4096, 1, 1)x(256, 1, 1), Context 1, Stream 7, Device 0, CC 8.6
    Section: GPU Speed Of Light Throughput
    ----------------------- ------------- ------------
    Metric Name               Metric Unit Metric Value
    ----------------------- ------------- ------------
    DRAM Frequency          cycle/nsecond         7.29
    SM Frequency            cycle/nsecond         1.41
    Elapsed Cycles                  cycle       702997
    Memory Throughput                   %        49.37
    DRAM Throughput                     %         0.01
    Duration                      usecond       498.66
    L1/TEX Cache Throughput             %         1.25
    L2 Cache Throughput                 %        49.37
    SM Active Cycles                cycle    698143.45
    Compute (SM) Throughput             %         1.57
    ----------------------- ------------- ------------
```
# Resoruces
- https://developer.nvidia.com/blog/even-easier-introduction-cuda/
- https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html
- https://resources.nvidia.com/en-us-nsight-developer-tools/nsight-compute-ui-cli-guide?lx=P1ZhhI&topic=hpc
- https://docs.nvidia.com/cuda/wsl-user-guide/index.html
- https://www.youtube.com/playlist?list=PL5B692fm6--ukF8S7ul5NmceZhXLRv_lR