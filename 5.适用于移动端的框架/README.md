### 一、常用移动端深度学习框架

各大公司开源了自己的移动端深度学习框架，其中包括TensorFlow Lite、Caffe2、MACE、paddle-mobile(MDL)、FeatherCNN、NCNN等。我们参考开源的测试结果，结合自己整理的数据，针对主流的异动单深度学习框架进行简单对比及介绍。


| 框架 | 机构 | 支持平台 | Stars | Forks | 
| --------------------------------------------------------- | ----------- | -------------- | ---------- | ----- |
| [Caffe2](https://github.com/caffe2/caffe2)                | Facebook    | ARM            |    8270*   | 2080* |
| [TF_Lite](https://github.com/tensorflow)                  | Google      | ARM            |     *      |   *   |
| [MACE](https://github.com/XiaoMi/mace)                    | Xiaomi      | ARM/DSP/GPU    |    2442    |  412  |
| [paddle-mobile](https://github.com/PaddlePaddle/paddle-mobile)      | Baidu       | ARM/GPU        |    4038    |  774  |
| [FeatherCNN](https://github.com/Tencent/FeatherCNN)       | Tencent     | ARM            |    658     |  170  |
| [NCNN](https://github.com/Tencent/ncnn)                   | Tencent     | ARM            |    4606    | 1163  |


###  二、性能对比 (截至2018.09.11)

#### 1. NCNN / FeatherCNN / MACE

**CPU：kryo&2.15GHz*2  (ms)**  

| 框架    | SqueezeNet_v1.1 | MobileNet_v1  | ResNet18 
| --------------- | :------------------:  | :------------------:  | :-----:|
| NCNN            | 47.64                 | 68.71                 | 142.28 |
| FeatherCNN      | 36.39                 | 58.92                 | 100.13 |
| MACE            | 42.37                 | 65.18                 | 160.7  |


#### 2. paddle-mobile 

**CPU：高通835  (ms)**  

| 框架             | squeezenet | mobilenet_v1 | googlenet_v1
| ---------------- | :--------: | :----------: | :----------: |
| 1 Thread         | 82.41      | 105.43       | 341.25       |
| 2 Threads        | 56.17      | 62.75        | 233.35       |
| 4 Threads        | 36.45      | 37.13        | 158.55       |


### 三、框架评价

| 框架  |集成成本| 库文件大小 | 模型支持程度 | 文档完整程度 | 速度 |
| ------------------ | :----: | :-----: | :----: | :-----: | :----: | 
| caffe2             | 一般   | 良好    | 优秀   | 良好    | 一般   | 
| TF_Lite            | 一般   | 良好    | 优秀   | 良好    | 优秀   | 
| MACE               | 良好   | 优秀    | 良好   | 良好    | 优秀   | 
| MDL                | 优秀   | 优秀    | 良好   | 良好    | 良好   | 
| FeatherCNN         | 良好   | 优秀    | 良好   | 良好    | 优秀   |
| NCNN               | 优秀   | 优秀    | 良好   | 优秀    | 优秀   | 


### 四、几款移动端深度学习框架分析

移动端的框架，基本不支持训练，只支持前向推理。


#### 1.腾讯的FeatherCNN和ncnn

这两个框架都是腾讯出的，FeatherCNN来自腾讯AI平台部，ncnn来自腾讯优图。

重点是：都开源，都只支持cpu

ncnn开源早点，文档、相关代码丰富一些，使用者相对多一些。FeatherCNN开源晚，底子很好，从测试结果看，速度具有微弱优势。


#### 2.百度的 paddle-mobile(MDL)
 
MDL支持cpu和gpu的，FPGA在开发中。

#### 3.小米的 MACE

它有几个特点：异构加速、汇编级优化、支持各种框架的模型转换。

小米支持的GPU不限于高通，这点很通用，很好，比如瑞芯微的RK3299就可以同时发挥出cpu和GPU的好处来。

#### 4.其它

在移动端，caffe2、tensorflow lite都可以考虑，只是可能没有以上的框架效率高。

另外据说支付宝有xNN的深度框架，商汤有PPL框架，这两个都是企业自用没有开源。

国内杭州九言科技的开源方案，用的人不多，可以参考。

#### 5.总结

上面的大部分框架都是主要面向android的，但是用于arm-Linux也是可以的。

现在越来越多的厂商开源移动端的深度学习框架，对于从业者是好事，有更多的选择，不用从头造轮子。

相信将来会有更多的技术手段用于移动端部署深度学习网络，包括模型压缩、异构加速、汇编优化等。


### 五、推荐框架

针对目前开源的移动端深度学习前向框架，结合我们使用、测试的结果，我们推荐以下几个框架。

#### 1.NCNN

第一个高效使用的移动端开源库，支持模型丰富，更新快，文档逐渐完善，被大家采用较多，遇到坑相对少。

#### 2.MACE

性能优秀，支持GPU，但是刚刚开源，可能会遇到一些开发问题。

#### 3.MDL

百度出品，一定的品质保证，更新较快。

### 参考资料

[移动端深度学习框架小结](https://blog.csdn.net/yuanlulu/article/details/80857211)

[NCNN性能分析](https://www.zhihu.com/question/276372408)

[NCNN性能对比](https://www.zhihu.com/question/263573053)

[MACE、NCNN、FeatherCNN性能对比](https://www.zhihu.com/question/283022477/answer/430168888)
