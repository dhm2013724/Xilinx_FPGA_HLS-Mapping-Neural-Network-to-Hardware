# 示例：如何将目标检测算法YOLOv2映射到Xilinx FPGA Zedboard
由于目前处于Deadline时期，要等下个礼拜才有时间把完整的整个流程在Github上分享一下，现在只能先用中文简单描述一下整个流程：从Darknet 框架中的YOLOv2模型到最终生成bitstream的过程。  
（1）需要先从Darknet官网下载darknet框架，然后将其中YOLOv2的权重提取出来。由于YOLOv2的卷积层基本都会跟着BatchNormalization，所以在提取权重的过程中，就将YOLOv2中的weight和bias分别和对应的BN乘在一起具体公式可以参考文献[1]，公式如下：  
y=(x-bn0)/sqrt(bn1) (1)  
z=sc0*y+sc1         (2)  
所以，可以将(1)与(2)合并，得到：  
            y=A*x+B (3)  
其中 A= sc0/sqpr(bn1), B=sc1-sc0*bn0/sqrt(bn1)  
这部分代码放在framework目录下  


参考文献：
[1] [An Automatic RTL Compiler for High-Throughput FPGA Implementation of Diverse Deep Convolutional Neural Networks](https://ieeexplore.ieee.org/document/8056824/)  
