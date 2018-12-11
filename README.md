# [Inception V3](https://github.com/tfzoo/InceptionV3) 

[![sites](tfzoo/tfzoo.png)](http://www.tfzoo.com)

## [简介](https://github.com/tfzoo/InceptionV3/wiki) 

### 网络结构
```
   name        		| new name
  =======================================
  conv0             | Conv2d_1a_3x3
  conv1             | Conv2d_2a_3x3
  conv2             | Conv2d_2b_3x3
  pool1             | MaxPool_3a_3x3
  conv3             | Conv2d_3b_1x1
  conv4             | Conv2d_4a_3x3
  pool2             | MaxPool_5a_3x3
  mixed_35x35x256a  | Mixed_5b
  mixed_35x35x288a  | Mixed_5c
  mixed_35x35x288b  | Mixed_5d
  mixed_17x17x768a  | Mixed_6a
  mixed_17x17x768b  | Mixed_6b
  mixed_17x17x768c  | Mixed_6c
  mixed_17x17x768d  | Mixed_6d
  mixed_17x17x768e  | Mixed_6e
  mixed_8x8x1280a   | Mixed_7a
  mixed_8x8x2048a   | Mixed_7b
  mixed_8x8x2048b   | Mixed_7c
  
```

#### 第1卷积层

输入：

```
# 299 x 299 x 3

end_point = 'Conv2d_1a_3x3'
net = slim.conv2d(inputs, depth(32), [3, 3], stride=2, scope=end_point)
end_points[end_point] = net
if end_point == final_endpoint: return net, end_points

batch_size = 5
height, width = 299, 299

#inputs: a tensor of size [batch_size, height, width, channels].
inputs = tf.random_uniform((batch_size, height, width, 3))


```

slim的conv2d构造的是一个激活函数为Relu的卷积神经网络

```
w_conv1 = weight_variable([5, 5, 1, 32])
b_conv1 = bias_variable([32])
h_conv1 = tf.nn.relu(conv2d(x_image, W_conv1) + b_conv1)
h_conv1 = slim.conv2d(x_image, 32, [5, 5])

```

#### 第2卷积层

输入（对应第1卷积输出）：

```
# 149 x 149 x 32
end_point = 'Conv2d_2a_3x3'
net = slim.conv2d(net, depth(32), [3, 3], scope=end_point)
end_points[end_point] = net
if end_point == final_endpoint: return net, end_points

```

#### MaxPool

将卷积参数进行减少，单纯的进行特征图的压缩不改变深度，可以使用步长和宽度计算公式，获得输出层的高度和宽度。


#### dropout层

随机除去一些神经元，使整个模型不至于过拟合，参数设定keep_prob = 0.8(保留80%的神经元)。

#### FullConnect层

全连接层，在整个过程的最后，才使用全连接，训练出权重。

#### softmax层

神经网络最后是softmax层，softmax层是分类专用的层，使用概率来表示待分类对象有多大概率属于某个类。


---

###  www.tfzoo.com 
###  qitas@qitas.cn
