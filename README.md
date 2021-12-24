# [ADCNN](https://github.com/tfmcu/ADCNN)

[![sites](http://182.61.61.133/link/resources/head.png)](http://www.STOPs.top)

## [简介](http://www.OS-Q.com/ADCNN)

[ADCNN](https://github.com/tfmcu/ADCNN)试图通过MCU的ADC输入进行数据深度分析处理，实现数据的前置判断和中断事件。


### TODO

* 基于MCU ADC DMA数据获取
* 前置CNN数据获取和传输
* CNN模型的下载和运行框架
* 特征提取和中断机制

### CNN

卷积神经网络CNN的结构一般包含这几个层：

* 输入层：用于数据的输入
* 卷积层：使用卷积核进行特征提取和特征映射
* 激励层：由于卷积也是一种线性运算，因此需要增加非线性映射
* 池化层：进行下采样，对特征图稀疏处理，减少数据运算量。
* 全连接层：通常在CNN的尾部进行重新拟合，减少特征信息的损失
* 输出层：用于输出结果


当然中间还可以使用一些其他的功能层:

* 归一化层（Batch Normalization）：在CNN中对特征的归一化
* 切分层：对某些（图片）数据的进行分区域的单独学习
* 融合层：对独立进行特征学习的分支进行融合


### MCU


* [STM32G474](https://docs.soc.xin/STM32G474) 5x 12bit ADC (5 Msps)

* [STM32H730](https://docs.soc.xin/STM32H730) 2x 16bit ADC (3.6 Msps) + 12bit ADC (5 Msps)

更多 [ADC](https://docs.soc.xin/for/adc) 相关器件
