# Data_sampling_for_compression
Research that sampling method can accelerate to find the optimal configuations by 
[LibPressio](https://github.com/robertu94/libpressio)
## There are four kinds of sampling method
* Block-wise Maximum sampling method
* Block-wise Minimum sampling method
* Block-wise Random sampling method
* Discrete Wavelet transformation (DWT) sampling method  
  
For all of the sampling method, user can setup level to adjust the block size and the wavelet scale. For example, if input data is 2D, then it is sampled by 2^level^2 block size or the value of level scale in DWT. if input data is 3D, then 2^level^3 block size.
## Visualization Analysis
* Block-wise Maximum sampling method. 

  The method samples the maximum value in each block from the original data. For visualization, it cannot keep the visual quailty. Put the sampled data into SZ compressor and fix the error boundary. In both level=1 and 2, its PSNR and compression ratio decreases dramatically.
  
* Block-wise Minimum sampling method. 

  The method samples the minimum value in each block from the original data. For visualization, it cannot keep the visual quailty. Put the sampled data into SZ compressor and fix the error boundary. Because of the numerical distribution of PRECIPf48.bin.f32 from Hurricane ISABEL dataset in 
[SDRbemch](https://sdrbench.github.io), where most of the values concentrate in the range(0, 1e-4), the method in level 1 and 2 have better performance in PSNR and compression ratio.
  
*  Block-wise Random sampling method. 

The method randomly samples values in each block from the original data. For visualization, it has the worst visual quailty. Put the sampled data into SZ compressor and fix the error boundary, it maintains the quality of PSNR when the level becomes larger.

* DWT sampling method. 

  it maintains the realtion of each original data point. When the value of level scale becomes larger, some low-frequency data is filtered out. For visualization, DWT sampling method keeps the visual quality. Put the sampled data into SZ compressor and fix the error boundary. In level scale=1, its PSNR maintains the. same quality as the orignal data, but the compression ratio decreases. In level scale=2, its PSNR slightly decreases, but the compression ratio dramatically decreases.
