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

#### CMSIS-NN

CMSIS (Cortex Microcontroller Software Interface Standard) 基于Arm Cortex处理器的微控制器的独立于供应商的硬件抽象层

CMSIS-NN用于在Cortex M上进行神经网络学习，CMSIS-RTOSv1用于实时操作系统的通用API以及基于RTX的参考实现，CMSIS-Core（M）用于Cortex-M处理器内核和外围设备的标准化API。


CMSIS-NN库包含两个部分： NNFunction和NNSupportFunctions。

NNFunction包含实现通常神经网络层类型的函数，比如卷积（convolution），深度可分离卷积（depthwise separable convolution），全连接（即内积inner-product）， 池化（pooling）和激活（activation）这些函数被应用程序代码用来实现神经网络推理应用。 内核API也保持简单，因此可以轻松地重定向到任何机器学习框架。NNSupport函数包括不同的实用函数，如NNFunctions中使用的数据转换和激活功能表。 这些实用函数也可以被应用代码用来构造更复杂的NN模块，例如， 长期短时记忆（LSTM）或门控循环单元（GRU）。


https://github.com/ARM-software/CMSIS_5/tree/develop/CMSIS/NN
