# FPGAs
Amazon EC2 F1 instances are available today in three different sizes that include up to eight Virtex® UltraScale+ VU9P FPGAs with a combined peak compute capability over 170 TOP/sec (INT8). 

Guiding Ideas:
Matrix Vector Multiplication should be performed in a row wise fashion:
  - Scaling by each entry then adding is: 1000 Multiplications Followed by 999 Addditions. 
  - Dot Product: 1000 Multiplications In Parallel. (Approx half the work)
  - Use DSP to parallelize.
