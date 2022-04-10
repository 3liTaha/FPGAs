# FPGAs
Amazon EC2 F1 instances are available today in three different sizes that include up to eight Virtex® UltraScale+ VU9P FPGAs with a combined peak compute capability over 170 TOP/sec (INT8). 

Guiding Ideas:
Matrix Vector Multiplication should be performed in a row wise fashion:
  - Scaling by each entry then adding is: 1000 Multiplications and an Accumulator (good way) approx 1000 Cycles (2000 DSP Slices in Series one for accumulator, one for multiplication). 
  - Dot Product: 1000 Multiplications In Parallel. Followed by 10 cycles for addition (bad way) (Requires memory)
  - JIT Memory Loading: Vector for next multiplication loaded as next multiplication starts ( during first round, stays there after).
  - Use DSP to parallelize.

Workflow for Development Software Defined Acceleration:
  1. Implement Design Using Vitis
  2. Emulate Using Software Emulation For Correctness
  3. Emulate Using Software Emulation For Profiling
  4. Generate Binaries
  5. Run on FPGA.

Tools to Use:
  - Vitis CLI
  - Vitis Analyzer

Current plan:
  1. Accelerate Dot Product to take one clock cycle with critical path starting at memory going through DSPs and ending in memory.
  2. Measure performance doing each dot product on FPGA
  3. Adjust design to reduce memory transfers in FPGA

Good Resources/ Introductory Material For Vitis and the development Environment For Acceleration:
  1. https://github.com/Xilinx/Vitis-Tutorials/tree/2021.2/Getting_Started/Vitis
  2. https://docs.xilinx.com/v/u/2019.2-English/ug1393-vitis-application-acceleration: Read First four chapters Save a lot of time.
