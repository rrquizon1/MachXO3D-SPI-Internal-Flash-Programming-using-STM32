This is an SSPI Internal Flash programming example using STM32F411

This example uses STM32F411 using STM32 HAL SPI Drivers and GPIO control for CS similar to previous Raspberry Pi 5 SPI example.

The instructions used in this program follows the guideline of FPGA-TN-02069-1.7(MachXO3D Programming and Configuration User Guide)

In this implementation you can modify the array in spi_data.c with your own bitstream.

![image](https://github.com/user-attachments/assets/513da793-7d51-4f61-b058-81fd711c09fa)

The internal flash has different configuration sectors such as CFG0, CFG1, and the feature row. In this implementation, I included functions to program CFG0, CFG1, and the feature row.
![image](https://github.com/user-attachments/assets/f4312b2e-80e2-4edf-9346-e2f216fee9d2)

See sample console printing below:
![image](https://github.com/user-attachments/assets/dc502ad6-be00-4f2c-86f4-9f67c3673d6e)

Some challenges for STM32 implementation:
1.  Limited Storage on STM32F411: Unlike the Raspberry Pi, which offers significantly more storage, the STM32F411 Discovery board has only 512 KB of internal flash. With an internal flash image size of approximately 260 KB for a 9400-density device, this allows for just one image. However, when targeting lower-density devices, it may be possible to fit two images within the available memory. See below for the memory region allocation:
 ![image](https://github.com/user-attachments/assets/55e7d559-24bb-4c6d-ae8b-6539bf7576d3)

2. Optimized Verification Process: To improve efficiency and reliability, the verify operation was restructured to perform frame-by-frame verification, ensuring a more optimized and scalable implementation.




